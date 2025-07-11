---
layout: default
title: "✅ Pruebas iniciales del sistema"
parent: "02 – Instalación y configuración del sistema"
nav_order: 5
---

# ✅ Pruebas iniciales del sistema

Con los sistemas operativos instalados, los discos montados, Docker configurado y Samba funcionando, es fundamental realizar una serie de pruebas para asegurarse de que todo está operativo antes de desplegar servicios más complejos.

Esta página recopila comandos de comprobación, pruebas de red y verificaciones para ambos servidores (MSI y Raspberry Pi).

---

## 🌐 1. Verificación de red y conectividad

### 🔁 Ping entre dispositivos (LAN o Tailscale)
Desde un servidor al otro:
```bash
ping raspberry.local
ping msi.local
```
Desde el portátil Windows (Tailscale):
```powershell
ping msi
ping raspberry
```

> 💡 Asegúrate de que todos los dispositivos estén conectados a la VPN de Tailscale o a la misma red local.

---

## 🔑 2. Accesos por SSH

Desde el cliente (Windows con terminal o WSL):
```bash
ssh pi@raspberry
ssh msi@msi
```

Verifica que puedes acceder sin errores y que tienes permisos sudo si es necesario:
```bash
sudo -v
```

---

## 🧰 3. Comprobación de montaje de discos (Raspberry Pi)

Verifica con `df -h`:
```bash
df -h
```

Salida esperada (con rutas correctas):
```
/dev/sda1    /home/pi/hdd
/dev/sdb1    /home/pi/ssd1
```

Revisar UUIDs en `/etc/fstab` y asegurar persistencia tras reinicio:
```bash
cat /etc/fstab
```

---

## 📁 4. Acceso Samba desde Windows

Desde el explorador de archivos de Windows:
```
\\msi
\\raspberry
```

Montar como unidades de red si no se hace automáticamente. Probar lectura y escritura sobre carpetas compartidas.

---

## 🐳 5. Comprobación de Docker y contenedores

### Ver estado de Docker:
```bash
docker version
docker info
```

### Listar contenedores:
```bash
docker ps -a
```

### Lanzar contenedor de prueba (ej. Portainer):
```bash
docker run -d -p 9000:9000 --name=portainer \
  -v /var/run/docker.sock:/var/run/docker.sock \
  -v portainer_data:/data \
  portainer/portainer-ce
```

Acceder desde navegador:  
`http://<IP-o-hostname>:9000`

---

## 📋 6. Verificación general del sistema

- ✅ `ping` exitoso entre servidores
- ✅ Conexión SSH funcional
- ✅ Discos montados y persistentes
- ✅ Samba accesible desde Windows
- ✅ Docker y Portainer funcionando

> 🧠 Con todas estas pruebas superadas, tu infraestructura está lista para comenzar a desplegar servicios autoalojados de forma estructurada, segura y accesible.

---
