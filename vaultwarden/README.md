# Vaultwarden Docker Configuration

This folder contains the Docker Compose configuration I use to self-host Vaultwarden — a lightweight, Bitwarden-compatible password manager — as part of my homelab infrastructure.

Vaultwarden allows me to securely manage credentials and sensitive data while maintaining full control over where that data is stored and how it is accessed.

---

## 🔧 Overview

- **Platform:** Docker (managed via Portainer)
- **Hosting Location:** Hetzner Cloud ARM VM
- **HTTPS:** Managed internally via Nginx Proxy Manager with Let’s Encrypt
- **Access:** Private only — via VPN tunnel or Tailscale

---

## 🔐 Access Control

This Vaultwarden instance is **not exposed to the public internet**.

It is accessible only through:
- My **home network**, via a VPN tunnel using Gluetun
- **Tailscale**, which securely connects my devices to my private Tailnet

Ingress is handled by Nginx Proxy Manager, and HTTPS is enabled via Let’s Encrypt certificates. Hetzner firewall rules limit inbound access to Cloudflare IPs and prevent direct traffic to Vaultwarden.

---

## 📦 Files Included

| Filename                | Description                                    |
|-------------------------|------------------------------------------------|
| `docker-compose.yml`    | Main Docker Compose file for Vaultwarden       |
| `README.md`             | This file                                      |

---

## ⚙️ How to Deploy

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd vaultwarden
```
Start the Container
```bash
docker-compose up -d
```
🔄 Backup
This docker compose file includes vaultwarden-backup. This container is used to backup vaultwarden on a regular basis.
