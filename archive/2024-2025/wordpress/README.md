# WordPress Docker Configurations

This folder contains Docker Compose files for two public WordPress sites that I self-host using Docker on a Hetzner cloud VM. Each site runs in its own container with isolated volumes and databases, and is routed via Nginx Proxy Manager with HTTPS provided by Let’s Encrypt.

These WordPress sites are production-ready and backed up automatically as part of my broader 3-2-1 backup strategy.

---

## 🌐 Sites Hosted

| Domain                          | Purpose                                |
|----------------------------------|----------------------------------------|
| [logand99.com](https://logand99.com)       | Personal portfolio & resume site       |
| [ramblingamblinpickem.com](https://ramblingamblinpickem.com) | Sports betting blog (seasonal project) |

---

## 🧱 Deployment Overview

- **Platform:** Hetzner Cloud ARM VM (separate from core homelab services)
- **Management:** Docker + Portainer
- **Reverse Proxy:** Nginx Proxy Manager (domain-based routing)
- **TLS:** Let’s Encrypt via NPM
- **Database:** MariaDB (containerized, per site)
- **Backups:** Daily with WP-Vivid, stored in Hetzner Storage Box and replicated to TrueNAS → Backblaze B2

---

## 📦 Files Included

| Filename                         | Description                                          |
|----------------------------------|------------------------------------------------------|
| `docker-compose.logand99.yml`    | Docker Compose file for the portfolio site           |
| `docker-compose.pickem.yml`      | Docker Compose file for the sports blog              |
| `.env.example`                   | Template for managing secrets and config             |
| `README.md`                      | This documentation file                              |

---

## ⚙️ How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd wordpress
```
### 2. Set Up Environment Variables
```bash
cp .env.example .env
```
### 3. Start a Site
# For portfolio site
```bash
docker-compose -f docker-compose.logand99.yml up -d
```
# For sports blog
```bash
docker-compose -f docker-compose.pickem.yml up -d
```
