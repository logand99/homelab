# Draw.io (diagrams.net) Docker Configuration

This folder contains the Docker Compose configuration for my self-hosted instance of [Draw.io](https://www.draw.io/) (also known as diagrams.net).

I use Draw.io as my primary tool for creating network diagrams, architecture charts, and service maps to document my homelab and internal infrastructure visually.

---

## 🧩 Use Case: Visual Documentation for Homelab

Draw.io helps me:
- Map my home and cloud network topology
- Visualize Gluetun VPN routing and container relationships
- Design future changes before deploying them
- Include diagrams in other documentation tools like BookStack or GitHub

---

## 🧱 Deployment Details

- **Hosted On:** Hetzner Cloud ARM VM
- **Managed With:** Docker + Portainer
- **Access:** Routed through Nginx Proxy Manager (HTTPS optional)
- **Storage:** Diagrams are saved manually to shared storage (e.g., NAS or SMB mount)

---

## 📦 Files Included

| Filename             | Description                                |
|----------------------|--------------------------------------------|
| `docker-compose.yml` | Deploys the Draw.io container               |
| `README.md`          | This documentation file                    |

---

## ⚙️ How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd drawio
```
### 2. Start the Container
```bash
docker-compose up -d
```
