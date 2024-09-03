---
layout: default
title: "Fase de recoñecemento: escaneado de portos con Nmap"
date: 2024-09-02
---

Neste post, resumimos os tipos de escaneado de portos que existen para Nmap, e a súa optimización á hora de executalos.

Sabemos que os protocolos de L4 son TCP (con handshake en 3 pasos, SYN-SYN/ACK-ACK) ou UDP (sen handshake). Aínda así, distinguimos 3 tipos de escaneado.

* **TCP-conexión** (TCP Connect): Tenta establecer unha conexión a cada porto aberto con handshake en 3 pasos. É a única forma de escanear TCP sen privilexios de administrador (sudo ou dende root). Tras o handshake, envíase un RST,ACK para terminar a conexión.
* **TPC-SYN**: Forma de escaneado por defecto cando `nmap` se executa con privilexios administrativos. Desta volta, o handshake non se completa, senón que a resposta ao SYN/ACK do servidor é un RST,ACK para finalizar a conexión directamente. É un escaneo máis sixiloso e lixeiramente máis eficiente ca un TCP Conexión.
* **UDP**: Escanea UDP. Ao ser un protocolo que non espera unha resposta, baséase en respostas de IMCP 3 con erro. Cando o paquete é respostado con erro, indicaría que o porto está pechado. Un paquete que non obtén resposta pode indicar un porto aberto por regla xeral.

| Tipo de escaneado               | Comando de exemplo                                         |
|-------------------------|---------------------------------------------------------|
| TCP Conexión                | `nmap -sT IP_MAQUINA`                       |
| TCP SYN          | `sudo nmap -sS IP_MAQUINA`                       |
| UDP     | `nmap -sU IP_MAQUINA`                       |

Pódense combinar as procuras (por exemplo, usar as bandeiras -sT e -sU no mesmo comando).


Se non se especifica nada, nmap escaneará os primeiros 1000 portos. Outras opcións para optimizar as procuras:


| Opción | Descrición                            |
|--------|------------------------------------|
| -T{n}     | Vai dende T0 a T5. Un valor mais alto envía máis paquetes por segundo, a risco de perdelos cada vez que se incrementa a velocidade. O T0 é máis fiable, e máis complicado de detectar, pero é excesivamente lento. Nos CTF e durante a aprendizaxe usaremos T4 moitas veces. T3 é a opción por defecto. T1 é axeitado para entornos reais con obxectivos e contextos definidos.      |
| -p22,80     | Escanea os portos 22 e 80   |
| -p-    | Escanea os 65536 portos                |
| -p10000-30000    | Escanea do porto 10000 ao 30000 (inclusive)                |
| -F    | Escanea os 100 primeiros portos (Fast, escaneo rápido)               |
| --min-rate=64    | Número mínimo de paquetes por segundo (*probes*) fixado en 64            |
| --max-rate=100    | Número máximo de paquetes por segundo (*probes*) fixado en 100           |
| --min-parallelism=512    | Número mínimo de paquetes por segundo (*probes*) en paralelo fixado en 512            |
| --max-parallelism=512    | Número máximo de paquetes por segundo (*probes*) en paralelo fixado en 512           |
