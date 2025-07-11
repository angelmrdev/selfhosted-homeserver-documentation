---
layout: default
title: "Primeros pasos tras la instalación"
parent: "Instalación de sistemas y primeros pasos"
nav_order: 3
---

# 🔧 Primeros pasos comunes tras la instalación

Una vez instalados Ubuntu Server 24.04 en el MSI y Raspberry Pi OS Lite en la Raspberry Pi, es importante realizar una serie de pasos comunes para asegurar un entorno funcional, seguro y listo para desplegar servicios.

---

## 🛠️ 1. Actualizar e instalar utilidades esenciales

```bash
sudo apt update && sudo apt upgrade -y
sudo apt install git curl htop net-tools ufw
```

---

## 🌍 2. Configurar la zona horaria

```bash
sudo timedatectl set-timezone Europe/Madrid
```

---

## 🔌 3. Verificar conectividad de red

```bash
ip a
ping google.com
```

Asegúrate de que los dispositivos tienen conectividad LAN y salida a Internet.

---

## 🖥️ 4. Cambiar el hostname (si es necesario)

```bash
sudo hostnamectl set-hostname msi
# o en la Raspberry:
sudo hostnamectl set-hostname raspberry
```

---

## 🧱 5. Activar y configurar SSH

SSH suele estar habilitado por defecto en Ubuntu Server. En Raspberry Pi OS puede activarse con `raspi-config`:

```bash
sudo raspi-config
# -> Interface Options -> SSH -> Enable
```

Asegúrate de que el puerto 22 está disponible:

```bash
sudo ufw allow 22
sudo systemctl enable ssh
```

---

## 🔐 6. Crear un nuevo usuario (opcional)

```bash
sudo adduser usuario
sudo usermod -aG sudo usuario
```

---

## 🧹 7. Limpiar el sistema

Eliminar paquetes obsoletos y limpiar caché:

```bash
sudo apt autoremove -y
sudo apt clean
```

---

> ✅ Con esto, ambos sistemas quedan listos para montar discos, compartir carpetas y desplegar servicios autoalojados.
