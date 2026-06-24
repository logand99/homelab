# Tailscale Docker Configurations

This folder contains Docker Compose files for two Tailscale containers I use across my homelab infrastructure. Tailscale provides secure, encrypted connectivity between my home network, cloud-hosted services, and remote devices — without the need to expose any ports.

---

## 🔧 Overview

Tailscale is deployed in two key locations:

### 🏠 1. Home Network Instance
- **Compose File:** `docker-compose.home.yml`
- **Platform:** Raspberry Pi (Docker, Portainer)
- **Purpose:**
  - Advertises local home LAN subnets (e.g., `192.168.0.0/24`) to the Tailnet
  - Allows remote access to internal services like Pi-hole, Portainer, TrueNAS, and more
  - Enables SSH and browser access to internal IPs from anywhere without port forwarding

---

### ☁️ 2. Hetzner Cloud Instance
- **Compose File:** `docker-compose.hetzner.yml`
- **Platform:** Hetzner ARM VM (Docker, Portainer)
- **Purpose:**
  - Advertises the internal Docker network (`192.168.19.0/24`) to the Tailnet
  - Acts as a **fallback access method** for cloud services if public routes (e.g., via Nginx Proxy Manager) are unavailable
  - Securely connects cloud-hosted services to my private network without exposing ports

---

## 🌐 Features

- Encrypted peer-to-peer connectivity over WireGuard
- Subnet routing for seamless hybrid access
- No port forwarding required
- Integrated ACL and device authorization via the Tailscale admin dashboard

---

## ⚙️ How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd tailscale
```
Start the Tailscale Container
```bash
# Home Network
docker-compose -f docker-compose.home.yml up -d

# Hetzner Cloud
docker-compose -f docker-compose.hetzner.yml up -d
```
