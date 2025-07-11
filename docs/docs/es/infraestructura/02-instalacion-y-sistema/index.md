---
layout: default
title: "02 – Instalación y configuración del sistema"
parent: "Infraestructura y arquitectura"
nav_order: 2
has_children: true
---

# 🛠️ 02 – Instalación y configuración del sistema

Esta sección documenta el proceso de instalación y configuración base tanto del servidor MSI con Ubuntu Server 24 como de la Raspberry Pi con PiOS Lite. Incluye los pasos esenciales para dejar ambos sistemas listos para montar servicios, compartir recursos y trabajar en red.

---

## 🧱 1. Preparación del hardware

### 🔵 MSI (Ubuntu Server)
- Portátil MSI antiguo reconvertido en servidor.
- BIOS configurada para:
  - Arranque desde USB.
  - Wake on LAN (opcional).
- Sin entorno gráfico: instalación mínima.

### 🟢 Raspberry Pi
- Raspberry Pi 4 con fuente estable y disipación pasiva.
- Tarjeta microSD clase 10 (16GB o más) con PiOS Lite.
- Disco duro externo WD My Book de 4TB (USB).
- Tarjeta PCIe con 4 bahías SSD + 1 SSD de 1TB.
- Disco recuperado de portátil (HDD antiguo).

---

## 💿 2. Instalación de sistemas operativos

### Ubuntu Server 24.04 (MSI)
- ISO oficial descargada desde ubuntu.com.
- Instalación básica sin entorno gráfico.
- Usuario creado: `msi`
- SSH habilitado desde el inicio.

### Raspberry Pi OS Lite (Pi)
- Imagen descargada con Raspberry Pi Imager.
- Personalización antes del flasheo:
  - Activar SSH.
  - Configurar hostname.
  - Crear usuario `pi` con contraseña.
- Primer arranque con teclado y monitor o vía red.

---

## 🔐 3. Primeros pasos tras la instalación

### Comunes a ambos servidores:

Actualizar e instalar utilidades esenciales:

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl htop net-tools ufw
```

Configurar zona horaria:

```bash
sudo timedatectl set-timezone Europe/Madrid
```

Verificar conectividad de red:

```bash
ip a
ping google.com
```

Cambiar el hostname si es necesario:

```bash
sudo hostnamectl set-hostname nuevo-hostname
```

Reiniciar para aplicar cambios críticos:

```bash
sudo reboot
```

---

## 📦 4. Configuración de Samba

### MSI:

Instalar Samba:

```bash
sudo apt install samba
```

Configurar `/etc/samba/smb.conf`:

```ini
[msi]
path = /
browsable = yes
writeable = yes
guest ok = no
create mask = 0775
directory mask = 0775
valid users = msi
```

Crear usuario Samba:

```bash
sudo smbpasswd -a msi
```

### Raspberry Pi:

Compartir `/home/pi` y crear usuario Samba:

```bash
sudo apt install samba
sudo smbpasswd -a pi
```

---

## 🗃️ 5. Montaje de discos en la Raspberry Pi

Identificar discos:

```bash
lsblk
sudo blkid
```

Crear directorios de montaje:

```bash
sudo mkdir /home/pi/hdd
sudo mkdir /home/pi/ssd1
```

Editar `/etc/fstab` con UUID:

```fstab
UUID=xxxx-xxxx  /home/pi/hdd   ext4   defaults  0  2
UUID=yyyy-yyyy  /home/pi/ssd1  ext4   defaults  0  2
```

Montar y verificar:

```bash
sudo mount -a
df -h
```

---

## 🐳 6. Instalación de Docker en la Raspberry Pi

Instalar Docker:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

Añadir usuario `pi` al grupo `docker`:

```bash
sudo usermod -aG docker pi
```

Instalar Docker Compose:

```bash
sudo apt install docker-compose
```

Crear estructura de carpetas:

```bash
sudo mkdir -p /opt/docker/jellyfin
sudo mkdir -p /opt/docker/qbittorrent
```

---

## 🧪 7. Pruebas iniciales

Desde Windows:
- Montar `\msi` y `\raspberry` como unidades de red.

Desde red local:
- Acceder por IP o MagicDNS (si Tailscale ya está instalado).

Lanzar un contenedor simple:

```bash
docker run -d -p 9000:9000 --name=portainer \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
```

---

> ✅ Con esto, ambos servidores quedan operativos, accesibles y listos para comenzar a desplegar servicios y automatizaciones.
