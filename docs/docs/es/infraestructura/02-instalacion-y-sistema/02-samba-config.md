---
layout: default
title: "Configuración de Samba"
parent: "02 – Instalación y configuración del sistema"
nav_order: 2
---

# 📁 Configuración de Samba

Esta página describe cómo instalar y configurar **Samba** para compartir archivos en red entre sistemas Linux (Ubuntu Server y Raspberry Pi) y clientes Windows. Samba permite acceder a carpetas compartidas como si fueran unidades de red, facilitando la transferencia y gestión de archivos.

---

## 🧰 Instalación del servidor Samba

### Ubuntu Server y Raspberry Pi

Ejecuta en ambos:

```bash
sudo apt update && sudo apt install samba -y
```

---

## ⚙️ Configuración del archivo `smb.conf`

### Ubuntu Server (MSI)

Compartiremos el directorio raíz (`/`) para tener acceso completo desde la red:

```ini
[msi]
path = /
browsable = yes
writable = yes
guest ok = no
create mask = 0775
directory mask = 0775
valid users = msi
```

- **`path`**: define la ruta compartida.
- **`valid users`**: restringe el acceso al usuario `msi`.
- Requiere que el usuario `msi` exista y tenga contraseña en Samba.

### Raspberry Pi

Compartiremos `/home/pi`, donde se montarán los discos externos:

```ini
[pi]
path = /home/pi
browsable = yes
writable = yes
guest ok = no
create mask = 0775
directory mask = 0775
valid users = pi
```

---

## 👤 Creación de usuarios Samba

### Ubuntu Server

```bash
sudo smbpasswd -a msi
```

### Raspberry Pi

```bash
sudo smbpasswd -a pi
```

---

## 🔁 Reinicio del servicio

Después de configurar, reinicia Samba:

```bash
sudo systemctl restart smbd
```

Verifica que esté activo:

```bash
sudo systemctl status smbd
```

---

## 🧪 Pruebas desde Windows

1. Abre el Explorador de Archivos.
2. En la barra de direcciones, escribe:
   ```
   \\100.x.x.x\msi
   \\100.x.x.x\raspberry
   ```
3. Introduce las credenciales correspondientes (`msi` o `pi`).
4. Puedes asignar cada una como **unidad de red** permanente.

> ✅ Con Samba correctamente configurado, puedes acceder y gestionar archivos de forma remota desde cualquier sistema Windows u otro dispositivo compatible con SMB.

---

