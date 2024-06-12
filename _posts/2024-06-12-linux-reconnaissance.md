---
layout: default
title: "Fase de recoñecemento: recoñecemento post-foodhold en Linux"
date: 2024-06-12
---

# Recoñecemento post-foothold en Linux
Todos os comandos recollidos nesta páxina están dispoñibles en [formato de script único](https://piartz.github.io/blog-mpr//2024/06/12/script-recon-linux.html), que se pode executar dende calqueira directorio nun host cos permisos axeitados. 
## Información do Sistema

### Información Completa do Sistema
`uname -a`

### Información sobre a Distribución de Linux
`cat /etc/os-release`

### Nome do Host do Sistema
`hostnamectl`

### Información sobre a Distribución de Linux
`lsb_release -a`
Información de Usuarios e Grupos


### Nome do Usuario Actual
`whoami`

### UID, GID e Grupos do Usuario Actual
`id`

### Lista de Usuarios
`cat /etc/passwd`

### Lista de Grupos
`cat /etc/group`

## Procesos en Execución

### Todos os Procesos en Execución
`ps aux`

### Lista en Tempo Real dos Procesos
`top`

`htop`

## Conexións de Rede


### Configuración das Interfaces de Rede
`ifconfig`

`ip a`

### Portas Abertas e Conexións Activas
`netstat -tuln`

`ss -tuln`

### Ficheiros Abertos Relacionados con Internet
`lsof -i`

## Montaxes e Sistema de Ficheiros


### Uso do Espazo en Disco
`df -h`

### Sistemas de Ficheiros Montados
`mount`

### Información sobre Todos os Dispositivos de Bloque
`lsblk`

## Busca de Arquivos de Interese


### Busca Ficheiros por Nome
`find / -type f -name "nome_do_ficheiro"`

### Busca Directorios por Nome
`find / -type d -name "nome_do_directorio"`

## Ficheiros SUID


### Busca Ficheiros con Permisos SUID
`find / -perm -4000 2>/dev/null`

### Busca Ficheiros con Permisos SGID
`find / -perm -2000 2>/dev/null`

## Información de Paquetes


### Lista de Todos os Paquetes Instalados (Debian/Ubuntu)
`dpkg -l`

### Lista de Todos os Paquetes Instalados (RedHat/CentOS)
`rpm -qa`

## Servizos en Execución


### Lista dos Servizos en Execución
`systemctl list-units --type=service --state=running`

### Lista de Todos os Servizos
`service --status-all`
