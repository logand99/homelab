# Cloudflared Docker Configuration

This folder contains Docker Compose configurations for my self-hosted [Cloudflare Tunnels](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/). These tunnels allow me to securely expose select homelab services to the internet **without opening any inbound ports** on my firewall or router.

All traffic is encrypted and proxied through Cloudflare’s global network, and identity-based access control is handled using **Cloudflare Access policies**.

---

## 🔧 Deployment Overview

| Instance Location | Purpose                          | Managed With |
|-------------------|----------------------------------|--------------|
| Raspberry Pi      | Tunnel to home network services  | Portainer    |
| Hetzner Cloud VM  | Tunnel to cloud services         | Portainer    |

Each tunnel runs as a Docker container using the `cloudflared` image.

---

## 🔐 Security Model

All exposed services are protected with **Cloudflare Access** policies:

- Users must enter a **pre-approved email address**
- Cloudflare sends a **one-time access code** to verified users
- Requests from unapproved emails are denied (no code sent)
- Once authenticated, access is passed to the internal service (which may have its own login)

---

## 🌐 Exposed Services

| Service      | Location       | Tunnel Target | Notes                                |
|--------------|----------------|----------------|--------------------------------------|
| Guacamole    | Raspberry Pi   | HTTPS (internal) | Used for browser-based RDP access    |
| NTFY         | Raspberry Pi   | HTTPS (internal) | Homelab notifications over tunnel    |

> Note: Nginx Proxy Manager handles local routing, TLS is managed by Cloudflare at the edge.

---

## 📦 Files Included

| Filename                         | Description                                  |
|----------------------------------|----------------------------------------------|
| `docker-compose.yml`         | cloudflared tunnel docker-compose            |
| `README.md`                      | This file                                    |

---

## ⚙️ How to Deploy

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd cloudflared
```
### 2. Start the Tunnel
```bash
docker-compose -f docker-compose.yml up -d
```
