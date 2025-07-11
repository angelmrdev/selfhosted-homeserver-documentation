---
layout: default
title: "01 – Arquitectura general"
parent: "Infraestructura y arquitectura"
nav_order: 1
---

# 🖥️ 01 – Arquitectura general

Esta sección presenta una visión general de la arquitectura del homelab personal, compuesto por dos servidores físicos, conectividad privada mediante VPN y servicios autoalojados tanto ligeros como pesados. La infraestructura está diseñada para ser escalable, modular y segura, con foco en el autoaprendizaje y la productividad.

---

## 🧠 Filosofía del proyecto

Este homelab está diseñado con una mentalidad realista, accesible y práctica:

- 🖥️ **Reutilización de hardware secundario**: portátil MSI en desuso y Raspberry Pi, sin grandes inversiones.
- 🧠 **Aprendizaje técnico real y aplicable**: cada decisión refuerza habilidades como administrador de sistemas.
- ♻️ **Sostenibilidad y eficiencia**: distribución de servicios según consumo y función.
- 📚 **Documentación modular y replicable**: pensada para ser útil a otros sin comprometer seguridad ni privacidad.

---

## 🖥️ Servidores

### 🔵 MSI Ubuntu Server 24

- **Sistema operativo**: Ubuntu Server 24.04 (instalación limpia)
- **Usuario principal**: `msi`
- **Funciones principales**:
  - Automatización avanzada (n8n)
  - Generación de imágenes con IA (AUTOMATIC1111)
  - LLMs en local (OpenWebUI, KoboldCpp)
  - Backups y tareas programadas
- **Conectividad**:
  - Conectado a Tailscale (VPN segura)
  - Accesible desde LAN y desde Tailscale (MagicDNS)
- **Compartición de archivos**:
  - Carpeta compartida vía **Samba**: acceso completo al sistema (`/`)
  - Accesible desde Windows como unidad de red: `\\100.x.x.x\msi`

---

### 🟢 Raspberry Pi (PiOS + Docker)

- **Dispositivo base**: Raspberry Pi con Raspbian/PiOS actualizado
- **Discos conectados**:
  - HDD montado en `/home/pi/hdd`
  - SSD montado en `/home/pi/ssd1` (vía adaptador PCIe)
- **Funciones principales**:
  - Servicios ligeros y multimedia
  - Dashboard y herramientas de red
  - Proxy inverso y domótica
- **Conectividad**:
  - Conectado a Tailscale
  - También accesible vía LAN local
- **Compartición de archivos**:
  - Carpeta compartida vía **Samba**: `/home/pi`
  - Accesible desde Windows como `\\100.x.x.x\raspberry`

#### 🧰 Montaje de un NAS casero

Esta Raspberry Pi no solo aloja servicios ligeros, sino que también funciona como un pequeño **NAS doméstico** de bajo consumo. Se ha configurado así:

- **Sistema operativo**: PiOS Lite instalado sobre tarjeta microSD clase 10 (rendimiento aceptable para tareas básicas).
- **Almacenamiento**:
  - 🔌 **WD My Book 4TB (USB)** → montado en `/home/pi/hdd`
    - Uso: almacenamiento multimedia (Jellyfin) y descargas (qBittorrent)
  - ⚙️ **Tarjeta PCIe con 4 bahías SSD**:
    - **SSD 1TB** → montado en `/home/pi/ssd1`
      - Uso: copia de seguridad de fotos y vídeos de Immich
    - **HDD reciclado** de un portátil antiguo (añadido a futuro)

- **Montajes permanentes** configurados con UUID en `fstab` para garantizar persistencia entre reinicios.
- **Compartido por Samba** → toda la ruta `/home/pi` está accesible desde Windows como unidad de red (`\\raspberry`).

> Esta configuración convierte la Pi en una **solución NAS eficiente y económica**, ideal para centralizar archivos y mantener backups automáticos, sin necesidad de invertir en un NAS dedicado.

---

### 💻 Portátil Windows (cliente)

- **Sistema**: Windows 10/11
- **Conectividad**:
  - Conectado a la red Tailscale
  - Acceso cifrado a ambos servidores sin abrir puertos
- **Accesos configurados**:
  - Unidades de red montadas: `\\msi` y `\\raspberry`
  - Interfaz web para servicios como Jellyfin, n8n, Immich, etc.

---

## 🔧 Consideraciones de diseño

**¿Por qué no usar Docker en el MSI?**  
Prefiero instalaciones manuales para servicios con uso intensivo de GPU o hardware, como AUTOMATIC1111 o LLMs.

**¿Por qué centralizar contenedores en la Pi?**  
Permite aislamiento, ligereza y facilidad de gestión gracias a Docker. Ideal para servicios livianos y pruebas.

**¿Por qué este hardware?**  
Es un enfoque **económico, funcional y formativo**, aprovechando equipos secundarios para construir un sistema completo.

---

## 🌐 Red y conectividad

- **VPN mesh con Tailscale**
  - Conexión cifrada entre servidores y cliente
  - Acceso remoto desde cualquier lugar
  - Uso de MagicDNS (`nombre.tailnet.ts.net`)
- **Acceso LAN local**
  - Para máxima velocidad en red doméstica
  - Funciona como fallback si VPN no está disponible
- **Sin puertos abiertos en router**

> 🔐 Toda la arquitectura está pensada para ofrecer **privacidad y seguridad sin exponer servicios a internet público**.

---

## 📊 Diagramas técnicos

Consulta la carpeta [`/diagrams`](../../../diagrams) para ver los esquemas del sistema:

- `topologia-red.drawio`: conexión entre dispositivos
- `arquitectura-almacenamiento.drawio`: discos, montajes y backups

---

## 🧾 Resumen general

| Elemento           | Descripción                                      |
|--------------------|--------------------------------------------------|
| **Servidores**     | MSI con Ubuntu + Raspberry Pi con PiOS          |
| **Cliente**        | Portátil Windows conectado por Tailscale        |
| **Red**            | VPN mesh + LAN opcional                         |
| **Almacenamiento** | Samba + montajes persistentes por UUID         |
| **Accesos**        | Web UI, SSH y unidades de red                   |

---

> 🛠️ Esta arquitectura es dinámica. Cualquier cambio se documentará en los siguientes artículos.
