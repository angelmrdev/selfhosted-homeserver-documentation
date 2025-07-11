---
layout: default
title: "03 – Red, VPN y acceso remoto"
parent: "Infraestructura y arquitectura"
nav_order: 3
has_children: true
---

# 🌐 03 – Red, VPN y acceso remoto

Esta sección aborda cómo conectar de forma segura con los servidores del HomeLab tanto desde la red local como desde el exterior, sin necesidad de abrir puertos en el router ni usar una IP pública.

Se documentan las herramientas y configuraciones utilizadas para establecer una red privada cifrada con Tailscale, acceder remotamente a través de SSH y SFTP, y montar unidades compartidas por Samba desde cualquier sistema cliente.

---

## 📂 Subpáginas

- [🔒 Tailscale y VPN Mesh](03-1-tailscale.md)  
  Explicación e instalación de Tailscale en Ubuntu y Raspberry Pi, configuración de MagicDNS y pruebas de conexión remota.

- [🖥️ Acceso remoto por SSH y FTP](03-2-acceso-ssh-ftp.md)  
  Conexión desde Windows y Linux usando SSH, claves, acceso mediante SFTP y configuración de clientes como FileZilla.

- [📁 Montaje de unidades Samba desde clientes](03-3-montaje-unidades.md)  
  Cómo montar carpetas compartidas por Samba desde Windows y Linux, incluyendo montaje automático y credenciales seguras.

---

> 🔐 El objetivo de esta sección es asegurar el acceso remoto y la compartición de recursos de forma segura, sin exponer servicios al exterior.
