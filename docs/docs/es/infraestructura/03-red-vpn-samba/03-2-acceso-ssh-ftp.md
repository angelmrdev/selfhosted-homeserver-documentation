---
layout: default
title: "Acceso remoto: SSH y FTP"
parent: "03 – Red, VPN y acceso remoto"
nav_order: 2
---

# 🧑‍💻 Acceso remoto: SSH y FTP

Esta página explica cómo acceder a los servidores del HomeLab de forma remota y segura utilizando dos protocolos ampliamente soportados: **SSH** para terminal y **FTP** para transferencia de archivos.  
Ambos métodos pueden usarse desde la red local o a través de Tailscale desde cualquier lugar.

---

## 🔐 Acceso remoto por SSH

### 1. Acceder al servidor Ubuntu (MSI)

```bash
ssh msi@nombre.tailnet.ts.net
```

O desde red local o vpn:

```bash
ssh msi@192.168.x.x
```

> 💡 Puedes guardar el nombre del host en `~/.ssh/config` para simplificar el acceso.

### 2. Acceder a la Raspberry Pi

```bash
ssh pi@nombre.tailnet.ts.net
```

> 🧠 Si usas autenticación por clave pública, puedes copiar tu clave con `ssh-copy-id`.

---

## 📂 Acceso por FTP con FileZilla

### 1. Configurar conexión en FileZilla

- **Protocolo**: SFTP - SSH File Transfer Protocol
- **Servidor**: `nombre.tailnet.ts.net` o IP local o IP VPN
- **Usuario**: `pi` o `msi`
- **Puerto**: `22` (puede cambiar si lo has personalizado)

> ✅ Asegúrate de que el servidor SSH esté habilitado y el firewall permita la conexión.

### 2. Explorar archivos

Una vez conectado, puedes ver el sistema de archivos remoto y transferir carpetas entre el servidor y tu equipo local.

---

## 🧾 Notas de seguridad

- Cambia las contraseñas por defecto (`pi`, `msi`).
- Usa claves SSH en lugar de contraseñas si es posible.
- Revisa los logs con `journalctl -u ssh` si algo falla.
- Considera cambiar el puerto por defecto del SSH.

---

> 🚀 El acceso remoto es uno de los pilares del HomeLab. Gracias a Tailscale, puedes mantener el acceso cifrado y seguro sin abrir puertos ni exponer IPs públicas.
