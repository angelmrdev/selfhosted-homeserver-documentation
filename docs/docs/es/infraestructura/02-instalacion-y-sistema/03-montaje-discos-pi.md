---
layout: default
title: "🧱 Montaje de discos en la Raspberry Pi"
parent: "02 – Instalación y configuración del sistema"
nav_order: 3
---

# 🧱 Montaje de discos en la Raspberry Pi

Esta guía explica cómo montar discos duros y SSD de forma permanente en la Raspberry Pi, usando UUID para asegurar que los montajes se mantengan tras reinicios. El objetivo es centralizar el almacenamiento y hacerlo accesible por red mediante Samba.

---

## 🔍 1. Identificar los discos

Conecta los discos externos y ejecuta los siguientes comandos para ver su estructura:

```bash
lsblk
sudo blkid
```

- `lsblk`: muestra los dispositivos y particiones montadas.
- `blkid`: proporciona el UUID necesario para `fstab`.

---

## 🗂️ 2. Crear directorios de montaje

Por convención, usaremos el home del usuario `pi`:

```bash
sudo mkdir /home/pi/hdd
sudo mkdir /home/pi/ssd1
```

Estos serán los puntos donde montaremos los discos:

- `/home/pi/hdd` → disco duro USB
- `/home/pi/ssd1` → SSD conectado por PCIe

---

## ✍️ 3. Editar el archivo /etc/fstab

Utiliza los UUID obtenidos con `blkid` y edita `/etc/fstab`:

```bash
sudo nano /etc/fstab
```

Ejemplo de entrada:

```fstab
UUID=xxxx-xxxx  /home/pi/hdd   ext4   defaults  0  2
UUID=yyyy-yyyy  /home/pi/ssd1  ext4   defaults  0  2
```

> Asegúrate de reemplazar los UUID con los reales. No montes discos en `/media/` si quieres compartirlos por Samba.

---

## ✅ 4. Montar y verificar

Aplica los cambios con:

```bash
sudo mount -a
```

Verifica que los discos estén montados:

```bash
df -h
```

Deberías ver las rutas `/home/pi/hdd` y `/home/pi/ssd1` correctamente montadas.

---

## 📁 5. Comprobación desde Samba

Si ya has configurado Samba para compartir `/home/pi`, podrás ver los discos accediendo desde Windows:

- `\raspberry\pi\hdd`
- `\raspberry\pi\ssd1`

> Asegúrate de que los permisos de los directorios montados sean correctos para evitar errores de acceso.

---

> 🧠 El uso de `fstab` con UUID permite reiniciar la Raspberry sin perder el acceso a los discos, lo que es fundamental para un sistema estable y accesible por red.
