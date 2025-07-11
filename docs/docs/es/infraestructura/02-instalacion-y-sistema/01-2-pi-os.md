---
layout: default
title: "Instalación de Raspberry Pi OS Lite"
parent: "Instalación de sistemas y primeros pasos"
nav_order: 2
---

# 🟩 Instalación de Raspberry Pi OS Lite

Esta guía cubre el proceso completo para instalar Raspberry Pi OS Lite en una Raspberry Pi 4, dejarla accesible por red y lista para montar discos y servicios básicos.

---

## 🧱 Requisitos previos

- Raspberry Pi 4 con disipador pasivo y fuente estable.
- microSD clase 10 (mínimo 16 GB) con lector USB o adaptador SD.
- Un ordenador con Raspberry Pi Imager instalado.

---

## 💿 Descarga y flasheo de imagen

1. Descarga **Raspberry Pi Imager** desde [raspberrypi.com/software](https://www.raspberrypi.com/software/).
2. Inserta la tarjeta microSD en tu equipo.
3. Abre Raspberry Pi Imager y selecciona:
   - **OS**: Raspberry Pi OS Lite (64-bit)
   - **Storage**: tu tarjeta microSD
4. Haz clic en el engranaje ⚙️ para activar opciones avanzadas:
   - Activar SSH
   - Establecer nombre de host (ej. `raspberrypi`)
   - Crear usuario (`pi`) y contraseña
   - Configurar zona horaria y WiFi (opcional si usas red cableada)
5. Flashea la imagen en la tarjeta.

---

## 🧪 Primer arranque

1. Inserta la microSD en la Raspberry Pi.
2. Conecta red (cable) y alimentación.
3. La Pi arrancará automáticamente y estará accesible por red local.
4. Usa `ping raspberrypi.local` o revisa tu router para ver la IP asignada.
5. Accede por SSH:
```bash
ssh pi@raspberrypi.local
```
(o usa la IP local si no funciona `.local`)

---

## 🛠️ Comprobaciones tras el arranque

- Comprueba que puedes hacer ping a Internet:
```bash
ping google.com
```
- Actualiza el sistema:
```bash
sudo apt update && sudo apt upgrade -y
```
- Instala utilidades básicas:
```bash
sudo apt install git curl htop net-tools ufw
```

---

> ✅ Con esto, tu Raspberry Pi ya está lista para compartir archivos, montar discos o instalar Docker y servicios autoalojados.
