# Gluetun VPN Container Configurations

This folder contains two Docker Compose configurations for Gluetun, a containerized VPN client. I use Gluetun in my homelab to:

1. Securely tunnel traffic between my Hetzner-hosted Docker services and my home network via WireGuard
2. Route selected containers' internet traffic through ProtonVPN for privacy

---

## 🛠️ Use Case 1: Site-to-Site VPN Tunnel (Hetzner → Home Network)

**Goal:**  
Enable services running in the cloud (Hetzner) to communicate securely with my home LAN.

### Key Components:
- **WireGuard Server:** Hosted on Ubiquiti Dream Machine Pro (UDM Pro)
- **Gluetun Client:** Running in Docker on a Hetzner ARM VM
- **Docker Network (Cloud):** `192.168.19.0/24`
- **Home LAN:** `192.168.0.0/24`
- **VPN Tunnel Subnet:** `10.1.1.0/24`

### Routing Notes:
- DNAT on UDM Pro redirects traffic to Gluetun (`10.1.1.2`) for Docker subnet access
- Custom `iptables` post-rule script added to Gluetun to accept incoming connections from the home LAN

### Files:
- `docker-compose.wireguard.yml`
- `postrules.sh` — Custom iptables rule

---

## 🔒 Use Case 2: Container Traffic via ProtonVPN

**Goal:**  
Route selected Docker containers' outbound traffic through ProtonVPN, ensuring privacy and IP masking.

### Features:
- ProtonVPN credentials passed via `.env` file
- Containers joined to Gluetun's Docker network
- Kill-switch behavior: if VPN drops, traffic is blocked

### Files:
- `docker-compose.protonvpn.yml`
- `.env.example` — Template for ProtonVPN credentials

---

## 🔧 How to Use

### 1. Clone the repo and navigate to this folder:
```bash
git clone https://github.com/logandavis/homelab-docker-compose.git
cd gluetun
