---
layout: default
title: "02 – Instalación y configuración del sistema"
parent: "Infraestructura y arquitectura"
nav_order: 2
has_children: true
---

# ⚙️ 02 – Instalación y configuración del sistema

Esta sección cubre la instalación de los sistemas operativos, la configuración base de red y usuarios, el montaje de discos y la preparación de ambos servidores para autoalojar servicios.  
El objetivo es dejar todo listo para comenzar a desplegar servicios y automatizaciones de forma segura y estructurada.

---

## 🧱 1. Preparación del hardware

### 🔵 MSI (Ubuntu Server)
- Portátil antiguo reconvertido en servidor
- BIOS ajustada: arranque desde USB y (opcional) Wake on LAN
- Sin entorno gráfico → instalación mínima con SSH

### 🟢 Raspberry Pi (PiOS Lite)
- Raspberry Pi 4 con disipador pasivo y fuente estable
- microSD clase 10 + discos externos (USB y SSD por PCIe)
- Ideal para servicios ligeros y almacenamiento casero

---

## 📂 Subpáginas

- [💿 Instalación de sistemas y primeros pasos](01-instalacion-sistemas.md)  
  (Instalación de Ubuntu y PiOS, comandos básicos, configuración SSH y zona horaria)

- [📁 Configuración de Samba](02-samba-config.md)  
  (Instalación, edición de `smb.conf`, creación de usuarios y pruebas)

- [🧱 Montaje de discos en la Raspberry Pi](03-montaje-discos-pi.md)  
  (Uso de UUID, `fstab`, pruebas de montaje, estructura final)

- [🐳 Instalación de Docker + Docker Compose + Portainer](04-docker-setup.md)  
  (Instalación manual, configuración de usuario, estructura de carpetas, Portainer)

- [✅ Pruebas iniciales del sistema](05-pruebas-iniciales.md)  
  (Verificación de red, acceso remoto, Docker, Samba y estructura general)

---

> 🧠 Todos estos pasos se han documentado con capturas, comandos y ejemplos reales del homelab. Si tienes un portátil o Raspberry Pi disponible, puedes replicar todo el sistema con mínimas modificaciones.
