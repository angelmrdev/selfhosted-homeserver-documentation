---
layout: default
title: "Montaje de unidades de red"
parent: "03 – Red, VPN y acceso remoto"
nav_order: 3
---

# 📁 Montaje de unidades de red compartidas

Esta subpágina explica cómo montar de forma permanente las carpetas compartidas por Samba en los servidores (MSI y Raspberry Pi) como unidades de red desde otros dispositivos, especialmente desde un sistema Windows.

---

## 🧠 ¿Por qué montar unidades de red?

Montar una unidad de red permite acceder directamente a carpetas remotas desde el explorador de archivos, como si fueran discos duros locales. Esto es útil para:

- Transferir archivos fácilmente.
- Centralizar almacenamiento multimedia o backups.
- Acceder desde distintas aplicaciones sin usar FTP o SSH.

---

## 🖥️ En Windows: montar unidad de red

### 1. Abrir el explorador de archivos

Haz clic derecho en “Este equipo” → “Conectar a unidad de red”.

### 2. Introducir dirección del recurso

Usa la dirección de red del servidor compartido:

```plaintext
\nombre.tailnet.ts.net\msi
\nombre.tailnet.ts.net\raspberry
```

O la IP local (en red LAN):

```plaintext
\192.168.1.xx\msi
\192.168.1.xx\raspberry
```

### 3. Elegir letra de unidad y marcar "Reconectar al iniciar sesión"

### 4. Introducir usuario y contraseña de Samba

- Para MSI: usuario `msi`
- Para Raspberry Pi: usuario `pi`

Puedes guardar las credenciales para no tener que introducirlas cada vez.

---

## 🧪 Alternativa temporal (CMD)

Puedes montar una unidad desde línea de comandos:

```cmd
net use Z: \\raspberry\pi /user:pi
```

---

## 🧰 Recomendaciones adicionales

- Si usas **Tailscale**, puedes montar las unidades con el nombre MagicDNS del servidor.
- Asegúrate de que el **servicio Samba esté activo** en ambos servidores.
- Verifica que las **rutas estén correctamente definidas** en `smb.conf`.
- Si tienes errores de permisos, revisa que el usuario Samba tenga acceso al recurso.

---

> ✅ Una vez montadas, podrás acceder a los archivos como si estuvieran en un disco físico. Esto facilita mucho la gestión diaria y el trabajo colaborativo en red.
