---
layout: default
title: "Instalación de Docker, Docker Compose y Portainer"
parent: "02 – Instalación y configuración del sistema"
grand_parent: "Infraestructura y arquitectura"
nav_order: 4
---

# 🐳 Instalación de Docker, Docker Compose y Portainer

Esta guía detalla el proceso para instalar Docker, Docker Compose y Portainer en la Raspberry Pi, dejando el sistema preparado para gestionar contenedores de forma eficiente y accesible.

---

## 🐚 Instalación de Docker

Docker puede instalarse fácilmente con un script oficial:

```bash
curl -fsSL https://get.docker.com -o get-docker.sh
sudo sh get-docker.sh
```

Después de la instalación, añade el usuario `pi` al grupo `docker`:

```bash
sudo usermod -aG docker pi
```

> 🔄 Reinicia la sesión (`logout/login`) o reinicia la Pi para aplicar el cambio de grupo.

---

## ⚙️ Verificación

Comprueba que Docker está correctamente instalado:

```bash
docker --version
docker run hello-world
```

---

## 🧱 Instalación de Docker Compose

```bash
sudo apt update
sudo apt install docker-compose
```

Verifica la versión instalada:

```bash
docker-compose --version
```

---

## 📁 Estructura de carpetas

Recomendamos crear una estructura de carpetas organizada en `/opt/docker/`:

```bash
sudo mkdir -p /opt/docker/jellyfin
sudo mkdir -p /opt/docker/qbittorrent
sudo mkdir -p /opt/docker/portainer
```

Puedes gestionar los archivos `docker-compose.yml` desde aquí para cada servicio.

---

## 📦 Instalación de Portainer

Portainer proporciona una interfaz gráfica para gestionar contenedores:

```bash
docker volume create portainer_data

docker run -d   -p 9000:9000   --name=portainer   --restart=always   -v /var/run/docker.sock:/var/run/docker.sock   -v portainer_data:/data   portainer/portainer-ce
```

Accede a Portainer desde el navegador en:

```
http://<IP_DE_TU_PI>:9000
```

Configura tu usuario administrador al primer acceso.

---

## 🔒 Seguridad

- Evita exponer el puerto 9000 a internet público.
- Puedes restringir el acceso mediante VPN (ej. Tailscale) o red local.
- Para añadir seguridad adicional, considera usar NGINX Proxy Manager con contraseña.

---

> ✅ Con estos pasos, tu Raspberry Pi estará lista para desplegar y administrar servicios Docker de forma cómoda y centralizada.
