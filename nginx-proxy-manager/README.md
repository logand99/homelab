# Nginx Proxy Manager (NPM) Docker Configurations

This folder contains Docker Compose files for all three of my Nginx Proxy Manager instances, which are used to manage reverse proxying, HTTPS, and access control across my homelab and cloud infrastructure.

NPM is a core part of my networking architecture — enabling secure, domain-based routing to both private and public services.

---

## 🌐 Overview of Instances

### 🏠 1. Home Network Instance

- **Compose File:** `docker-compose.home.yml`
- **Hosted On:** Raspberry Pi 5 (Docker, Portainer)
- **Purpose:**  
  - Provides internal HTTPS access to services via subdomains (e.g., `portainer.home.logand99.com`)
  - Uses Let’s Encrypt for certificates
  - Handles LAN service routing with clean URLs

---

### ☁️ 2. Hetzner Cloud (Internal Services)

- **Compose File:** `docker-compose.hetzner.yml`
- **Hosted On:** CAX31 ARM VM in Hetzner Cloud
- **Purpose:**  
  - Routes cloud services back to my home network via VPN
  - Container is attached to the same Docker network as my Gluetun VPN container
  - Acts as a secure reverse proxy across a single WireGuard tunnel

---

### 🌍 3. Public Services Instance

- **Compose File:** `docker-compose.public.yml`
- **Hosted On:** CAX11 ARM VM in Hetzner Cloud
- **Purpose:**  
  - Hosts multiple public-facing websites on a single public IP
  - Works with Cloudflare DNS + WAF for security and TLS
  - Provides HTTPS via Let’s Encrypt
- **Sites Hosted:**  
  - [logand99.com](https://logand99.com)  
  - [ramblingamblinpickem.com](https://ramblingamblinpickem.com)

---

## ⚙️ DNS & Routing Strategy

I use Cloudflare to manage DNS records and route subdomains to the appropriate NPM instance:

| Subdomain | Points To |
|-----------|-----------|
| `*.home.logand99.com` | Home NPM (Pi) |
| `*.cloud.logand99.com` | Hetzner NPM (VPN) |
| `logand99.com`, `ramblingamblinpickem.com` | Public NPM (Cloud VM) |

Each NPM instance manages HTTPS using Let’s Encrypt, and routes to internal services via Docker networking.

---

## 📦 How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logandavis/homelab-docker-compose.git
cd nginx-proxy-manager
```
Launch an instance
```bash
# Home
docker-compose -f docker-compose.home.yml up -d

# Hetzner Cloud (VPN-connected)
docker-compose -f docker-compose.hetzner.yml up -d

# Public Services
docker-compose -f docker-compose.public.yml up -d
```
⚠️ Make sure each NPM instance has its own mounted data directory for persistence.

🔐 Security Notes
Public NPM instance is secured via Cloudflare WAF — inbound access is only allowed from Cloudflare IP ranges

Let’s Encrypt certs are automatically provisioned and renewed

All NPM containers are only accessible via defined IPs or tunnels (depending on role)

Ensure proper rate limiting and authentication for public admin panels
