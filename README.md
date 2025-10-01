# 🏠 Selfhosted Homelab · Documentación Técnica

Bienvenido/a a la documentación técnica de mi proyecto personal de servidor casero. Este homelab está diseñado con el objetivo de aprender, optimizar y ofrecer soluciones reales para el autoalojamiento de servicios, la automatización de tareas, la inteligencia artificial local y el almacenamiento seguro en red.

> 🔧 Proyecto 100% funcional desplegado sobre una Raspberry Pi y un portátil con Ubuntu Server, conectados mediante VPN cifrada, con servicios accesibles desde cualquier lugar.

---

## 🧠 Filosofía del proyecto

- ✅ **Accesible y reutilizable**: basado en hardware disponible en casa
- 🧪 **En constante evolución**: documentación viva y modular
- 🔐 **Privacidad y control total**: sin depender de la nube comercial
- 🧰 **Aprendizaje aplicado**: Docker, automatización, AI, redes privadas

---

## 📚 Documentación principal

> La documentación está organizada en bloques temáticos dentro de la carpeta [`/docs/es`](docs/es/). Puedes explorar cada sección según la parte del sistema a la que hace referencia.

### 🔧 Infraestructura y red
- [01 - Arquitectura general](docs/es/01-arquitectura-general.md)
- [02 - Instalación del sistema y preparación inicial](docs/es/02-instalacion-y-sistema.md)
- [03 - Red y conectividad (VPN, Tailscale, Samba)](docs/es/03-red-y-conectividad.md)

### 💾 Servicios autoalojados
- [04 - Servicios en la Raspberry Pi](docs/es/04-servicios-pi.md)
- [05 - Servicios en el servidor MSI](docs/es/05-servicios-msi.md)

### 🧠 Automatización y mantenimiento
- [06 - Monitorización, backups y estado del sistema](docs/es/06-monitorizacion.md)
- [07 - Automatización de flujos con n8n](docs/es/07-automatizacion.md)
- [08 - Troubleshooting: errores comunes y soluciones](docs/es/08-troubleshooting.md)

---

## ⚙️ Archivos de configuración Docker

> Todos los servicios están definidos en contenedores separados dentro de `/docker`, con un script global para levantar toda la pila.

### Servicios Docker
- [`adguard-home/docker-compose.yml`](docker/adguard-home/docker-compose.yml)
- [`dashy/docker-compose.yml`](docker/dashy/docker-compose.yml)
- [`home-assistant/docker-compose.yml`](docker/home-assistant/docker-compose.yml)
- [`immich/docker-compose.yml`](docker/immich/docker-compose.yml)
- [`jellyfin/docker-compose.yml`](docker/jellyfin/docker-compose.yml)
- [`netdata/docker-compose.yml`](docker/netdata/docker-compose.yml)
- [`nginx-proxy-manager/docker-compose.yml`](docker/nginx-proxy-manager/docker-compose.yml)
- [`qbittorrent/docker-compose.yml`](docker/qbittorrent/docker-compose.yml)
- [`watchtower/docker-compose.yml`](docker/watchtower/docker-compose.yml)

### Script general
- [`up-all.sh`](docker/up-all.sh): script único para levantar todos los servicios Docker definidos

---

## 🌍 Disponible también en inglés

Este proyecto está siendo traducido al inglés para hacerlo accesible a una comunidad más amplia:

👉 [View English version / Go to EN landing page](/readme-en.md)

---

## 📌 Sobre el autor

Soy técnico en sistemas y redes, con experiencia en automatización, servidores Linux, contenido digital y proyectos personales IT. Este homelab nació como necesidad y se ha convertido en un espacio de experimentación y aprendizaje aplicado.

🔗 [LinkedIn](https://www.linkedin.com/in/angelmr2711/)  
🔗 [Repositorio en GitHub](https://github.com/angelmrdev/selfhosted-homelab-documentation)

---

## 💬 Contacto y colaboración

¿Quieres montar tu propio servidor casero o implementar algo similar en tu entorno personal o profesional?

📩 Puedes escribirme o proponer mejoras mediante issues o pull requests en este repositorio.

---

## 🌐 Acceso web

Puedes consultar la versión web estilizada del proyecto aquí:

🔗 [https://angelmrdev.github.io/selfhosted-homelab-documentation/](https://angelmrdev.github.io/selfhosted-homeserver-documentation/)


---
