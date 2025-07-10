# 01 - Arquitectura general

Esta sección presenta una visión general de la arquitectura de mi homelab personal, compuesto por dos servidores físicos, conectividad privada mediante VPN y servicios autoalojados tanto ligeros como pesados. La infraestructura está diseñada para ser escalable, modular y segura, con foco en el autoaprendizaje y la productividad.

---

## 🧠 Filosofía del proyecto

Este homelab está diseñado con una mentalidad realista, accesible y práctica:

- 🖥️ **Reutilización de hardware secundario**: se utilizan equipos que ya tenía en casa (un portátil MSI en desuso y una Raspberry Pi), aprovechando al máximo sus capacidades sin necesidad de grandes inversiones.
- 🧠 **Aprendizaje técnico real y aplicable**: cada decisión del sistema está pensada para mejorar mis habilidades como administrador de sistemas, automatizador y self-hoster.
- ♻️ **Sostenibilidad y eficiencia**: los servicios están distribuidos en función del consumo energético, uso real y escalabilidad.
- 📚 **Documentación modular y replicable**: todo el proyecto está estructurado para que otros puedan aprender o replicarlo fácilmente, sin exponer datos privados.


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

Esta configuración convierte la Pi en una **solución NAS eficiente y económica**, ideal para centralizar archivos y mantener backups automáticos, sin necesidad de invertir en un NAS dedicado.

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

### ❓Sobre los servidores

**¿Por qué no uso Docker en el MSI?**  
El MSI ejecuta servicios más complejos como AUTOMATIC1111 o n8n con integración directa de hardware (GPU), por lo que prefiero tener un control total sobre el sistema mediante instalaciones manuales.

**¿Por qué centralizar los contenedores en la Raspberry Pi?**  
La Raspberry Pi, aunque más modesta, es perfecta para ejecutar servicios ligeros y contenerizados. Gracias a Docker, puedo aislar, actualizar y gestionar cada servicio sin comprometer el rendimiento general.

**¿Por qué elegir un MSI viejo y una Pi?**  
Porque es un enfoque económico y sostenible. Este proyecto está pensado para **sacar partido a hardware secundario**, útil para formarse, experimentar y tener control total sobre tu red y tus datos.

---

## 🌐 Red y conectividad

- **VPN privada con Tailscale**
  - Conexión cifrada entre todos los dispositivos
  - Acceso remoto incluso fuera de la LAN
  - Uso de MagicDNS (ej: `raspberry.tailnet-name.ts.net`)
- **Alternativa LAN local**
  - Conexión directa cuando todos los dispositivos están en la misma red local
  - Configurado como fallback si Tailscale no está disponible
- **Sin puertos abiertos en router**
  - Máxima privacidad y seguridad

---

### ❓ Sobre la red

**¿Por qué uso Tailscale como base de red?**  
Tailscale permite crear una VPN mesh segura y cifrada entre dispositivos sin necesidad de abrir puertos ni complicarse con el router. Es ideal para un entorno doméstico con alta seguridad.

**¿Por qué tener acceso LAN además de VPN?**  
Aunque Tailscale cubre todos los casos, tener acceso LAN local asegura compatibilidad y velocidad máxima en caso de que la VPN no esté disponible o haya cambios en la red.

**¿Es seguro este tipo de montaje?**  
Sí. No se expone ningún puerto públicamente. Todo el acceso está restringido a mi red privada, protegida por la autenticación de Tailscale y el aislamiento de cada servicio.

---

## 📊 Diagramas técnicos

Consulta la carpeta [`/diagrams`](../../diagrams) para ver los esquemas de red y almacenamiento del proyecto:

- `topologia-red.drawio` – Diagrama de conexión entre dispositivos
- `arquitectura-almacenamiento.drawio` – Distribución de discos, puntos de montaje y backups

---

## 🧾 Resumen

| Elemento         | Descripción breve                                          |
|------------------|------------------------------------------------------------|
| **Servidores**   | MSI con Ubuntu Server y Raspberry Pi con PiOS             |
| **Cliente**      | Portátil Windows conectado por Tailscale                   |
| **Red**          | VPN con MagicDNS + LAN opcional                            |
| **Almacenamiento** | Compartido por Samba, discos externos montados por UUID |
| **Accesos**      | Desde Windows, interfaces web, y SSH                       |

---

> 🛠️ Esta arquitectura está en constante evolución. Los cambios o ampliaciones se documentarán en las siguientes secciones.
