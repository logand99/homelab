# Pi-hole Docker Configurations

This folder contains Docker Compose files for two of my four Pi-hole instances. These are containerized and managed through Portainer.

I use these instances for:

- DNS filtering and ad-blocking
- Local DNS record management
- Split-DNS architecture between cloud and home networks

All instances are synced using [nebula-sync]([https://github.com/paperbenni/nebula-sync](https://github.com/lovelaze/nebula-sync)).

---

## 📍 Instances Covered

### 1. Raspberry Pi 5 Instance
- Location: Home network
- Platform: ARM, Docker, Portainer
- Compose File: `docker-compose.rpi5.yml`

### 2. Hetzner Cloud VM Instance
- Location: Hetzner Cloud (ARM)
- Platform: Docker, Portainer
- Compose File: `docker-compose.hetzner.yml`

---

## 📦 How to Use

Clone this repo:
```bash
git clone https://github.com/logandavis/homelab-docker-compose.git
cd pihole
```
Start a Pi-hole instance:
```bash
docker-compose -f docker-compose.rpi5.yml up -d
```
