---
layout: default
title: "Documentation in English"
nav_order: 3
has_children: true
---

# 📘 Technical Documentation · English Version

Welcome to the full technical documentation of this **self-hosted personal HomeLab project**. Here you'll find guides, examples and configurations to help you set up and maintain your own home server using modern, efficient and secure technologies.

> 🚧 This documentation is a work in progress and will be expanded continuously.

---

## 🧱 Infrastructure and Architecture

> Initial setup, home network, hardware and connectivity between devices.

- [01 – General architecture](infrastructure/01-general-architecture.md)
- [02 – Base system installation](infrastructure/02-system-installation.md)
- [03 – Network, VPN and sharing (Tailscale, Samba)](infrastructure/03-network-connectivity.md)

---

## 🗃️ Self-hosted Services

> All services are deployed using Docker, categorized by server (Raspberry Pi or MSI).

- [04 – Services on Raspberry Pi](services/04-raspberry-services.md)
- [05 – Services on the MSI server](services/05-msi-services.md)

---

## 🤖 Automation and Local AI

> Task automation with n8n, custom flows and local AI experimentation.

- [06 – Automating flows with n8n](automation/06-n8n.md)
- [07 – Getting started with local AI models](automation/07-local-ai.md)

---

## 🔐 Security, Backups and Monitoring

> System monitoring, automatic backups, alerts and service protection.

- [08 – Monitoring with Netdata](security/08-monitoring.md)
- [09 – Backup and restore strategies](security/09-backups.md)
- [10 – Security best practices](security/10-security.md)

---

## 💡 Use Cases and Extensions

> Real use cases: multimedia, syncing, remote access, and small business tools.

- [11 – Personal media center](usecases/11-media-center.md)
- [12 – Remote access and home office](usecases/12-remote-office.md)
- [13 – Tools for freelancers and small businesses](usecases/13-freelance-smb.md)

---

## 📦 Additional Resources and Annexes

> Scripts, configurations, useful resources and external links.

- [14 – Docker files](resources/14-docker.md)
- [15 – Utility scripts](resources/15-scripts.md)
- [16 – References and recommended reading](resources/16-references.md)

---

## 📌 About this Project

This HomeLab is deployed using a Raspberry Pi and an Ubuntu-based server, connected via encrypted VPN and accessible from anywhere. It's designed to combine learning with real-world, replicable solutions for personal or professional use.

If you're interested in building something similar, check out the [GitHub repository](https://github.com/angelmrdev/selfhosted-homeserver-documentation) or feel free to reach out and contribute.

---
