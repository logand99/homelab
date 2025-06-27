# Plex Media Server Docker Configuration

This folder contains Docker Compose files for two instances of Plex that I self-host as part of my homelab and cloud infrastructure. Plex is used to organize and stream my personal collection of movies, TV shows, music, and ebooks — with a focus on reliability, secure access, and storage efficiency.

---

## 🎬 Use Case: Personal Media Streaming

I use Plex to:
- Stream my personal media collection to devices on my network and remotely
- Maintain metadata, watch history, and multiple user profiles
- Enable mobile access through the official Plex apps
- Keep media redundant with a backup server on-prem

---

## 🌐 Deployment Overview

| Instance       | Platform         | Role              | Notes                                  |
|----------------|------------------|-------------------|----------------------------------------|
| `primary`      | Hetzner Cloud VM | Main media server | Accesses home network via Gluetun VPN  |
| `backup`       | Raspberry Pi 5   | Local fallback    | Used when remote server is offline     |

- Both instances mount the same media directory via **SMB** from a Hetzner Storage Box
- Containers are managed using **Portainer**

---

## 📦 Files Included

| Filename                   | Description                                  |
|----------------------------|----------------------------------------------|
| `docker-compose.primary.yml` | Main Plex server hosted in Hetzner Cloud     |
| `docker-compose.backup.yml`  | Backup/local Plex server on Raspberry Pi     |
| `.env.example`              | Template for credentials and config values   |
| `README.md`                | This documentation file                      |

---

## ⚙️ How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logandavis/homelab-docker-compose.git
cd plex
```
### 2. Set Up .env
```bash
cp .env.example .env
```
### 3. Start the Container
# Primary (Hetzner)
```bash
docker-compose -f docker-compose.primary.yml up -d
```

# Backup (RPi)
```bash
docker-compose -f docker-compose.backup.yml up -d
```
