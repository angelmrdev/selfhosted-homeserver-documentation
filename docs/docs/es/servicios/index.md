---
layout: default
title: "Servicios autoalojados"
nav_order: 2
parent: "Documentación en Español"
has_children: true
---

# 🗃️ Servicios autoalojados

En esta sección se documentan todos los servicios que forman parte del HomeLab, desplegados mediante Docker y organizados según el equipo en el que se ejecutan. Cada servicio se configura como un contenedor independiente, facilitando la gestión modular y escalable del sistema.

> 🐳 Se utiliza Docker Compose para definir, lanzar y mantener cada pila de servicios.

---

## 🧩 Organización

Los servicios se dividen según el dispositivo que los aloja:

- **Raspberry Pi**: servicios de red, dashboard, multimedia ligera y domótica.
- **Servidor MSI (Ubuntu Server)**: servicios más pesados, automatización, IA local, monitorización y backups.

---

## 📑 Índice de contenidos

- [04 – Servicios en Raspberry Pi](04-servicios-pi.md)  
  Dashy, Home Assistant, AdGuard Home, Immich, Jellyfin, NGINX Proxy Manager, etc.

- [05 – Servicios en el servidor MSI](05-servicios-msi.md)  
  n8n, modelos de IA, Netdata, Watchtower, y otras herramientas avanzadas.

---

## 🔧 Estado de desarrollo

✅ Artículos organizados por servidor  
🛠️ Documentación ampliable con nuevas pilas de servicios
