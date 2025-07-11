---
layout: default
title: "Tailscale y VPN Mesh"
parent: "03 – Red, VPN y acceso remoto"
nav_order: 1
---

# 🔒 Tailscale y VPN Mesh

Esta página documenta cómo instalar y configurar **Tailscale**, una solución de VPN mesh fácil de desplegar que permite conectar los dispositivos del HomeLab desde cualquier lugar del mundo sin necesidad de abrir puertos en el router ni contratar IP fija.

Con Tailscale se crea una red privada virtual entre nodos, usando el protocolo WireGuard, con acceso cifrado punto a punto y resolución de nombres mediante MagicDNS.

---

## ✅ ¿Por qué Tailscale?

- 🔐 **Seguridad**: cifrado extremo a extremo sin exponer puertos.
- 🌍 **Acceso remoto**: conecta tu HomeLab desde fuera de la red local.
- 🧠 **Fácil configuración**: sin reglas de firewall ni NAT complicadas.
- 🧩 **Multi-OS**: funciona en Linux, Windows, macOS, Android y más.
- 🧪 **Ideal para pruebas**: conexión entre dispositivos y despliegues locales.

---

## 💻 Requisitos previos

- Cuenta gratuita en [Tailscale](https://tailscale.com/)
- Acceso por terminal (SSH o físico) al servidor Ubuntu y a la Raspberry Pi
- Conexión a internet activa en ambos dispositivos

---

## 🧠 Conceptos clave

| Concepto       | Explicación                                                                 |
|----------------|------------------------------------------------------------------------------|
| **Tailnet**    | Tu red privada de dispositivos conectados por Tailscale                     |
| **MagicDNS**   | Resolución de nombres interna (ej: `raspberry.local.ts.net`)                |
| **ACLs**       | Control de acceso entre nodos (gestionado desde la web de Tailscale)        |
| **Key Auth**   | Permite unir nuevos dispositivos de forma automática                        |

---

## 🛠️ Instalación en Ubuntu Server 24

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

- Se abrirá un enlace que debes visitar en el navegador para autenticar el dispositivo.
- Una vez vinculado, aparecerá en tu [panel de administración](https://login.tailscale.com/admin/machines).

---

## 🛠️ Instalación en Raspberry Pi (PiOS)

```bash
curl -fsSL https://tailscale.com/install.sh | sh
sudo tailscale up
```

> 📌 Si estás usando PiOS Lite y no puedes abrir el navegador, puedes añadir el flag `--authkey` al comando `tailscale up` usando una **key de autenticación temporal** generada desde el panel web.

---

## ⚙️ Configuración opcional

### Activar inicio automático en ambos sistemas:

```bash
sudo systemctl enable --now tailscaled
```

### Ver estado y dirección IP privada:

```bash
tailscale status
```

---

## 🌐 Usar MagicDNS

Tailscale permite acceder a los dispositivos usando nombres amigables en lugar de IPs:

```bash
ping raspberry
ssh pi@raspberry
```

> 🧠 Esta funcionalidad se gestiona desde el panel de Tailscale, sección **DNS → MagicDNS**.  
> Asegúrate de que esté activada y que los nombres personalizados no tengan conflictos.

---

## 🔍 Ver y gestionar tu red privada

Accede a [login.tailscale.com/admin/machines](https://login.tailscale.com/admin/machines) para:

- Ver dispositivos activos
- Cambiar nombres y etiquetas
- Revocar accesos
- Generar claves de autenticación

---

## 🧪 Pruebas y uso básico

- Verifica conectividad entre nodos:
  ```bash
  ping raspberry
  ssh pi@raspberry
  ```

- Desde Windows:
  - Accede a servicios web (ej: `http://raspberry:8096` para Jellyfin)
  - Conecta unidades Samba con nombre del dispositivo (`\\raspberry`)

---

> 🔐 Tailscale permite una configuración robusta, segura y sin complicaciones, ideal para acceder al HomeLab desde cualquier lugar del mundo.
