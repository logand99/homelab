# Apache Guacamole Docker Configuration

This folder contains my Docker Compose setup for running Apache Guacamole — a browser-based remote desktop gateway. I use Guacamole to access headless Windows machines on my home network and as a tertiary access point into my homelab if VPN or Tailscale are unavailable.

---

## 🔧 Use Case: Remote Desktop Gateway

Guacamole allows me to:
- Access RDP sessions from any browser — no client required
- Manage Windows machines without local monitors or keyboards
- Maintain a fallback "jump box" into my home network when traditional VPN access is not an option

---

## 🌐 Deployment Overview

- **Hosted On:** Raspberry Pi 5
- **Managed With:** Docker + Portainer
- **Reverse Proxied Via:** Cloudflare Tunnel
- **Access Protocol:** RDP (Remote Desktop Protocol)
- **Secure Layers:**
  1. **Cloudflare Access Policy:** Only pre-approved emails can request a one-time access code
  2. **Guacamole Authentication:** Standard username + password login

---

## 📦 Files Included

| Filename              | Description                                      |
|-----------------------|--------------------------------------------------|
| `docker-compose.yml`  | Docker Compose file to deploy Guacamole          |
| `README.md`           | This documentation file                          |

---

## ⚙️ How to Deploy

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd guacamole
```
### 2. Start the Container
```bash
docker-compose up -d
```
