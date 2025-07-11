---
layout: default
title: "Instalación de Ubuntu Server 24.04"
parent: "Instalación de sistemas y primeros pasos"
nav_order: 1
---

# 🟦 Instalación de Ubuntu Server 24.04

Esta guía detalla el proceso de instalación del sistema operativo **Ubuntu Server 24.04 LTS** en un portátil MSI reutilizado como servidor principal del HomeLab.

> ⚠️ Se trata de una instalación mínima, sin entorno gráfico, orientada a rendimiento y seguridad en entorno autoalojado.

---

## 📥 1. Descarga de la ISO

- Página oficial: [https://ubuntu.com/download/server](https://ubuntu.com/download/server)
- Seleccionar la versión LTS (Long Term Support), en este caso **24.04**.
- Descarga la imagen `.iso`.

---

## 💽 2. Creación de USB booteable

Utiliza herramientas como:

- **Rufus** (Windows)
- **balenaEtcher** (Windows/macOS/Linux)
- **dd** (Linux avanzado)

> Asegúrate de seleccionar modo *MBR* si el BIOS no soporta UEFI.

---

## 🧰 3. Configuración previa en BIOS

- Accede al BIOS del portátil (generalmente con `F2`, `DEL` o `ESC`).
- Habilita:
  - Arranque desde USB
  - Wake on LAN (opcional)
  - Desactiva Secure Boot (si es necesario)
- Guarda cambios y reinicia con el USB conectado.

---

## 🖥️ 4. Instalación paso a paso

1. Arranca desde el USB.
2. Selecciona idioma e inicia instalación.
3. Configura:
   - Red (DHCP o IP fija)
   - Usuario administrador (ej: `msi`)
   - Nombre del equipo (`hostname`)
   - Particionado (automático o manual según disco)
4. Selecciona:
   - Instalar servidor OpenSSH (recomendado ✅)
   - No instalar paquetes de snap adicionales
5. Finaliza y reinicia.

> 💡 El servidor ya estará accesible por red vía SSH si la red y el router están configurados correctamente.

---

## 🔌 5. Conexión inicial por SSH

Desde otro equipo en la red local:

```bash
ssh msi@IP_LOCAL
```

Confirma que puedes acceder, actualiza el sistema y empieza la configuración básica.

---

> ✅ Ubuntu Server 24.04 ya está instalado, sin entorno gráfico, y listo para continuar con los primeros pasos comunes.
