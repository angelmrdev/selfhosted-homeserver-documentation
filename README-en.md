# Documentación del Homelab Personal Self-Hosted

Este repositorio documenta paso a paso el montaje, configuración y mantenimiento de mi servidor casero (homelab), distribuido entre dos máquinas físicas: una Raspberry Pi y un portátil MSI con Ubuntu Server 24. Está diseñado como una guía técnica reutilizable para quienes deseen montar su propio servidor local con servicios autoalojados, redes privadas y herramientas de automatización, IA o multimedia.

---

## 🧱 Arquitectura general

| Dispositivo       | Sistema            | Uso principal                                                   |
|------------------|--------------------|-----------------------------------------------------------------|
| **MSI (Servidor)** | Ubuntu Server 24   | IA, automatización, backups, servicios pesados, LLMs           |
| **Raspberry Pi** | Raspberry Pi OS     | Multimedia, red, proxy inverso, domótica, dashboard, DNS       |
| **Portátil Windows** | Windows 10/11     | Acceso remoto y gestión de archivos vía Samba y Tailscale      |

Ambos servidores están conectados mediante **VPN privada con Tailscale**, con acceso cifrado, sin necesidad de abrir puertos en el router. El portátil accede a ambos a través de Samba con unidades de red montadas.

---

## 🔧 Servicios desplegados

### Raspberry Pi (todo en Docker)
- 🎬 **Jellyfin** – Servidor multimedia local
- ⬇️ **qBittorrent** – Cliente torrent vía web
- 🖼️ **Immich** – Backup y gestión de fotos
- 📡 **NGINX Proxy Manager** – Proxy inverso y certificados
- 🧭 **Dashy / Homepage** – Dashboard de servicios
- 🔄 **Watchtower** – Actualización automática de contenedores
- 🧠 **AdGuard Home** – DNS local con bloqueo de anuncios
- 🏠 **Home Assistant** – Gestión domótica (futuro)
- 📈 **Netdata** – Monitorización del sistema

### MSI Ubuntu Server 24
- 🤖 **AUTOMATIC1111** – Generador local de imágenes con IA (Stable Diffusion)
- 🔁 **n8n** – Automatización de tareas (webhooks, APIs)
- 🧠 **OpenWebUI** – Interfaz para LLMs (Mistral, LLaMA, etc.)
- ✍️ **KoboldCpp** – Modelos de texto largo en local
- 📊 **Netdata** – Monitorización avanzada

---

## 🌐 Red y conectividad

- 🔒 VPN Tailscale entre todos los dispositivos
- 🧙 MagicDNS activado (ej. `raspberry.tailnet-name.ts.net`)
- 🔁 Acceso LAN directo alternativo disponible
- 💾 Acceso Samba desde Windows a:
  - `\\100.x.x.x\msi` → acceso completo a `/`
  - `\\100.x.x.x\raspberry` → acceso a `/home/pi` con discos montados

---

## 📂 Organización del repositorio

```
selfhosted-homelab-documentation/
├── README.md → Introducción en inglés
├── README.es.md → Introducción en castellano
├── LICENSE → Licencia MIT
├── .gitignore → Archivos ignorados por Git
│
├── docs/
│ ├── es/ → Manual completo en castellano (por secciones)
│ │ ├── 01-arquitectura-general.md
│ │ ├── 02-instalacion-y-sistema.md
│ │ ├── 03-red-y-conectividad.md
│ │ ├── 04-servicios-pi.md
│ │ ├── 05-servicios-msi.md
│ │ ├── 06-monitorizacion.md
│ │ ├── 07-automatizacion.md
│ │ ├── 08-troubleshooting.md
│ │ └── capturas-diagramas/
│ │ └── *.png
│ │
│ └── en/ → English documentation
│ ├── 01-architecture.md
│ ├── 02-setup-and-system.md
│ ├── 03-network-and-connectivity.md
│ ├── 04-pi-services.md
│ ├── 05-msi-services.md
│ ├── 06-monitoring.md
│ ├── 07-automation.md
│ ├── 08-troubleshooting.md
│ └── screenshots-diagrams/
│ └── *.png
│
├── docker/ → Archivos docker-compose por servicio
│ ├── jellyfin/
│ ├── qbittorrent/
│ ├── immich/
│ ├── nginx-proxy-manager/
│ ├── dashy/
│ ├── adguard-home/
│ ├── home-assistant/
│ ├── netdata/
│ ├── watchtower/
│ └── up-all.sh → Script para levantar todos los contenedores
│
├── diagrams/ → Diagramas técnicos editables (Draw.io, etc.)
│ ├── topologia-red.drawio
│ └── arquitectura-almacenamiento.drawio
```

---

## 👨‍💻 Objetivos del proyecto

- Documentar de forma clara y modular mi infraestructura real
- Demostrar habilidades de administración de sistemas, redes y contenedores
- Facilitar que otros puedan montar su propio homelab autoalojado
- Servir como ejemplo profesional en mi perfil de GitHub y LinkedIn

---

## 🧾 Licencia

Este proyecto está bajo licencia MIT. Puedes usarlo, adaptarlo o extenderlo libremente.
# 🏠 Selfhosted Homelab · Technical Documentation (EN)

> English version coming soon. In the meantime, feel free to explore the [original Spanish documentation](/index.md).

Follow me on [LinkedIn](https://www.linkedin.com/in/angelmr2711/) for updates.
