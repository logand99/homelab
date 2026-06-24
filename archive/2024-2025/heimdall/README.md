# Heimdall Docker Configuration

This folder contains Docker Compose files for two instances of Heimdall — a simple, self-hosted dashboard used to navigate and access services in my homelab and cloud environments.

Heimdall acts as the central launch point for my day-to-day system use.

---

## 🧩 Use Case: Dashboard for Homelab Services

Heimdall is used to:

- Organize links to internal and cloud-hosted services
- Provide a visual homepage for frequently accessed tools
- Separate **on-prem** and **cloud-based** resources for clarity
- Launch browser-based tools and dashboards quickly

---

## 🌐 Instances

| Instance   | Compose File               | Purpose                                 |
|------------|----------------------------|-----------------------------------------|
| On-Prem    | `docker-compose.onprem.yml`| Links to Pi-hole, Guacamole, Syncthing, etc. |
| Cloud      | `docker-compose.cloud.yml` | Links to Portainer, Vaultwarden, BookStack, etc. |

Each instance is deployed via Docker and managed with Portainer.

---

## 📦 Files Included

| Filename                    | Description                                        |
|-----------------------------|----------------------------------------------------|
| `docker-compose.onprem.yml` | Heimdall instance for local network services       |
| `docker-compose.cloud.yml`  | Heimdall instance for Hetzner-hosted cloud services |
| `README.md`                 | This file                                          |

---

## ⚙️ How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd heimdall
```
### 2. Start Heimdall
# On-premises instance
```bash
docker-compose -f docker-compose.onprem.yml up -d
```

# Cloud instance
```bash
docker-compose -f docker-compose.cloud.yml up -d
```

