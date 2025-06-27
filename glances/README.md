# Glances Docker Configuration

This folder contains the Docker Compose configuration I use to deploy [Glances](https://nicolargo.github.io/glances/) — a lightweight, web-based system monitoring tool. I run Glances on several key devices in my homelab to monitor system health, resource usage, and uptime in real time.

---

## 📈 Use Case: Homelab Health Monitoring

Glances provides:
- Real-time CPU, memory, disk, and network stats
- Web-based access to system metrics
- Cross-platform compatibility (ARM & x86)
- A single dashboard per device for at-a-glance diagnostics

---

## 📍 Devices Monitored

| Host            | Platform       | Notes                                   |
|------------------|----------------|-----------------------------------------|
| Raspberry Pi 5   | Docker on ARM  | Main Docker host (Portainer, Gluetun)  |
| Raspberry Pi 4   | Docker on ARM  | Primary Pi-hole server                  |
| Hetzner VM       | Docker on ARM  | Main cloud services node                |

Each host runs its own Glances container using the same Compose file, with minor local adjustments.

---

## 📦 Files Included

| Filename              | Description                                 |
|------------------------|---------------------------------------------|
| `docker-compose.yml`   | Main Glances deployment configuration       |
| `README.md`            | This documentation file                     |

---

## ⚙️ How to Deploy

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd glances
```
### 2. Start the Container
```bash
docker-compose up -d
```
