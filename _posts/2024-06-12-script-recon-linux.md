---
layout: default
title: "Script de recoñecemento post-foodhold en Linux"
date: 2024-06-12
---


# Script de recoñecemento en Linux

## Versión en inglés (Galego abaixo)

```
#!/bin/bash

echo "=== Post-Foothold Reconnaissance in Linux ==="

echo ""
echo "## System Information ##"
echo "1. Full System Information"
uname -a
echo ""

echo "2. Linux Distribution Information"
cat /etc/os-release
echo ""

echo "3. Hostname Information"
hostnamectl
echo ""

echo "4. Linux Distribution Information (Detailed)"
lsb_release -a
echo ""

echo "## User and Group Information ##"
echo "5. Current User Name"
whoami
echo ""

echo "6. Current User UID, GID, and Groups"
id
echo ""

echo "7. User List"
cat /etc/passwd
echo ""

echo "8. Group List"
cat /etc/group
echo ""

echo "## Running Processes ##"
echo "9. All Running Processes"
ps aux
echo ""

echo "10. Real-Time Process List"
top -bn1
echo ""

echo "## Network Connections ##"
echo "11. Network Interface Configuration"
ifconfig || ip a
echo ""

echo "12. Open Ports and Active Connections"
netstat -tuln || ss -tuln
echo ""

echo "13. Open Files Related to Internet"
lsof -i
echo ""

echo "## Mounts and Filesystem ##"
echo "14. Disk Space Usage"
df -h
echo ""

echo "15. Mounted Filesystems"
mount
echo ""

echo "16. Block Devices Information"
lsblk
echo ""

echo "## Search for Interesting Files ##"
echo "17. Search for Files by Name"
echo 'Run "find / -type f -name "filename" 2>/dev/null" to search for specific files.'
echo ""

echo "18. Search for Directories by Name"
echo 'Run "find / -type d -name "directoryname" 2>/dev/null" to search for specific directories.'
echo ""

echo "## SUID Files ##"
echo "19. Search for Files with SUID Permissions"
find / -perm -4000 2>/dev/null
echo ""

echo "20. Search for Files with SGID Permissions"
find / -perm -2000 2>/dev/null
echo ""

echo "## Package Information ##"
echo "21. List of Installed Packages (Debian/Ubuntu)"
dpkg -l 2>/dev/null || echo "Not a Debian/Ubuntu system"
echo ""

echo "22. List of Installed Packages (RedHat/CentOS)"
rpm -qa 2>/dev/null || echo "Not a RedHat/CentOS system"
echo ""

echo "## Running Services ##"
echo "23. List of Running Services"
systemctl list-units --type=service --state=running
echo ""

echo "24. List of All Services"
service --status-all 2>/dev/null || echo "Could not list all services"
echo ""

echo "Reconnaissance completed."
```
---
## Versión en galego

```
#!/bin/bash

echo "=== Recoñecemento post-foothold en Linux ==="

echo ""
echo "## Información do Sistema ##"
echo "1. Información Completa do Sistema"
uname -a
echo ""

echo "2. Información sobre a Distribución de Linux"
cat /etc/os-release
echo ""

echo "3. Información do Nome do Host"
hostnamectl
echo ""

echo "4. Información Detallada sobre a Distribución de Linux"
lsb_release -a
echo ""

echo "## Información de Usuarios e Grupos ##"
echo "5. Nome do Usuario Actual"
whoami
echo ""

echo "6. UID, GID e Grupos do Usuario Actual"
id
echo ""

echo "7. Lista de Usuarios"
cat /etc/passwd
echo ""

echo "8. Lista de Grupos"
cat /etc/group
echo ""

echo "## Procesos en Execución ##"
echo "9. Todos os Procesos en Execución"
ps aux
echo ""

echo "10. Lista en Tempo Real dos Procesos"
top -bn1
echo ""

echo "## Conexións de Rede ##"
echo "11. Configuración das Interfaces de Rede"
ifconfig || ip a
echo ""

echo "12. Portas Abertas e Conexións Activas"
netstat -tuln || ss -tuln
echo ""

echo "13. Ficheiros Abertos Relacionados con Internet"
lsof -i
echo ""

echo "## Montaxes e Sistema de Ficheiros ##"
echo "14. Uso do Espazo en Disco"
df -h
echo ""

echo "15. Sistemas de Ficheiros Montados"
mount
echo ""

echo "16. Información sobre Todos os Dispositivos de Bloque"
lsblk
echo ""

echo "## Busca de Arquivos de Interese ##"
echo "17. Busca Ficheiros por Nome"
echo 'Executa "find / -type f -name "nome_do_ficheiro" 2>/dev/null" para buscar ficheiros específicos.'
echo ""

echo "18. Busca Directorios por Nome"
echo 'Executa "find / -type d -name "nome_do_directorio" 2>/dev/null" para buscar directorios específicos.'
echo ""

echo "## Ficheiros SUID ##"
echo "19. Busca Ficheiros con Permisos SUID"
find / -perm -4000 2>/dev/null
echo ""

echo "20. Busca Ficheiros con Permisos SGID"
find / -perm -2000 2>/dev/null
echo ""

echo "## Información de Paquetes ##"
echo "21. Lista de Todos os Paquetes Instalados (Debian/Ubuntu)"
dpkg -l 2>/dev/null || echo "Non é un sistema Debian/Ubuntu"
echo ""

echo "22. Lista de Todos os Paquetes Instalados (RedHat/CentOS)"
rpm -qa 2>/dev/null || echo "Non é un sistema RedHat/CentOS"
echo ""

echo "## Servizos en Execución ##"
echo "23. Lista dos Servizos en Execución"
systemctl list-units --type=service --state=running
echo ""

echo "24. Lista de Todos os Servizos"
service --status-all 2>/dev/null || echo "Non se puido listar todos os servizos"
echo ""

echo "Recoñecemento completado."

```
