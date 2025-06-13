# BookStack Docker Configuration

This folder contains my Docker Compose setup for hosting BookStack — a self-hosted documentation platform used to organize and store technical notes, guides, and homelab documentation.

BookStack acts as my internal wiki for both professional knowledge and homelab infrastructure reference.

---

## 📘 Use Case: Personal Documentation Archive

BookStack is where I document:

- Complex or rarely-used system configurations (e.g., firewall rules, Linux tuning)
- Homelab service deployment notes
- Networking concepts and design patterns I've encountered professionally
- Quick CLI reference guides and troubleshooting procedures

---

## 🧱 Deployment Details

- **Hosted On:** Hetzner Cloud ARM VM
- **Managed With:** Portainer
- **Reverse Proxy:** Nginx Proxy Manager (with Let’s Encrypt TLS)
- **Access:** Private only via:
  - VPN (Gluetun to home)
  - Tailscale mesh VPN

---

## 📂 Files Included

| Filename              | Description                                 |
|-----------------------|---------------------------------------------|
| `docker-compose.yml`  | Main Docker Compose file for BookStack      |
| `README.md`           | This documentation file                     |

---

## ⚙️ How to Deploy

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd bookstack
```
### 2. Start the Container
```bash
docker-compose up -d
```
