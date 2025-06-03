# Pi-hole Docker Configurations

This folder contains Docker Compose files for two of my four Pi-hole instances, as well as the configuration for syncing all of them using [`nebula-sync`](https://github.com/lovelaze/nebula-sync).

These setups are part of a distributed DNS system I use across my homelab and cloud infrastructure.

---

## 📍 Pi-hole Instances Covered

### 1. Raspberry Pi 5 Instance
- **Location:** Home network
- **Platform:** ARM, Docker, Portainer
- **Compose File:** `docker-compose.rpi5.yml`

### 2. Hetzner Cloud VM Instance
- **Location:** Hetzner Cloud (ARM)
- **Platform:** Docker, Portainer
- **Compose File:** `docker-compose.hetzner.yml`

---

## 🔄 nebula-sync

[nebula-sync](https://github.com/lovelaze/nebula-sync) is used to synchronize Pi-hole configurations, blocklists, allowlists, and local DNS records across all four of my instances.

### nebula-sync Instance
- **Compose File:** `docker-compose.nebula-sync.yml`
- **Deployment:** Runs on my primary Raspberry Pi Pi-hole instance (or any trusted internal node)
- **Schedule:** Configured to sync at regular intervals via environment variables or cron inside the container

---

## 📦 How to Use

Clone this repo and navigate to the pihole folder:
```bash
git clone https://github.com/logandavis/homelab-docker-compose.git
cd pihole
```
Start a Pi-hole instance:
```bash
docker-compose -f docker-compose.rpi5.yml up -d
```
Start nebula-sync
```bash
docker-compose -f docker-compose.nebula-sync.yml up -d
```
