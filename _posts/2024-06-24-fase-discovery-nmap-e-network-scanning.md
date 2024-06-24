---
layout: default
title: "Fase de recoñecemento: escaneado de redes"
date: 2024-06-24
---

# Fase discovery: NMAP e escaneado da rede

## Escaneado de redes

###**Escanear tódolos host dunha rede**

`nmap -sn 192.168.1.0/24`

`netdiscover -r 192.168.0.1/24`

`fping -a -g 192.168.1.0/24`

**Con Metasploit**

```
sudo msfconsole
search discovery
use auxiliary/scanner/discovery/arp_sweep
show options
set RHOST 192.168.0.0/24
```

**Extración a ficheiro**

`sudo nmap -sn <IP> > nome_ficheiro.txt`

**Escaneado dende ficheiro**

`sudo nmap -iL target.txt -sn`



### **Searchsploit**

```
searchsploit -u # Para actualizar
searchsploit vsftpd
searchsploit -p <path>
python <path> <IP>
```



### **Escaneo agresivo**

`nmap -A <IP>`

**Gardar escaneo agresivo nun ficheiro**

`nmap -A <IP> -oX ficheiro.xml`

**Convertir ficheiro de output nun reporte HTML**

`xsltproc ficheiro.xml -o ficheiro.html`

### **Webmap**

Dashboard para resultados XML de `nmap`. Usar con Docker sempre, ver documentación no Github:

Descargar de [Github](https://github.com/SabyasachiRana/WebMap)



### Spoofing

**Spoofing de IP**

`sudo nmap -D -Pn <IP_falsa> <IP_host>`

**IP aleatoria**

`sudo nmap -D -Pn RND <Numero_IPs> <IP>`

**Spoofing de MAC**

`sudo nmap --spoof-mac O <IP_host>`

`sudo nmap --spoof-mac Apple <IP_host>`

**Spoof sen ping (Pn)**

`sudo nmap -Pn --spoof-mac O <IP_host>`
