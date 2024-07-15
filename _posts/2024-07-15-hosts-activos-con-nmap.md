---
layout: default
title: "Fase de recoñecemento: descubrimento de hosts activos con Nmap"
date: 2024-07-15
---

Neste post, vou resumir algúns comandos útiles de Nmap que emprego para explorar e auditar redes. Teño dúas táboas: unha cos diferentes tipos de escaneos que se poden facer e outra coas opcións máis comúns que uso.


| Tipo de escaneado               | Comando de exemplo                                         |
|-------------------------|---------------------------------------------------------|
| ARP Scan                | `sudo nmap -PR -sn IP_MAQUINA/24`                       |
| ICMP Echo Scan          | `sudo nmap -PE -sn IP_MAQUINA/24`                       |
| ICMP Timestamp Scan     | `sudo nmap -PP -sn IP_MAQUINA/24`                       |
| ICMP Address Mask Scan  | `sudo nmap -PM -sn IP_MAQUINA/24`                       |
| TCP SYN Ping Scan       | `sudo nmap -PS22,80,443 -sn IP_MAQUINA/30`              |
| TCP ACK Ping Scan       | `sudo nmap -PA22,80,443 -sn IP_MAQUINA/30`              |
| UDP Ping Scan           | `sudo nmap -PU53,161,162 -sn IP_MAQUINA/30`             |

**Nota:** Lembramos engadir `-sn` se soamente estamos interesados no descubrimento de hosts sen escaneado de portos (port-scanning). Se omitimos a bandeira `-sn`, Nmap executa por defecto o escaneado de portos.


| Opción | Descrición                            |
|--------|------------------------------------|
| -n     | sen procura reversa DNS (reverse lookup)                      |
| -R     | procura reversa para tódolos hosts   |
| -sn    | sóamente descubrimento de host                |
