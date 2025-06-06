# Gluetun VPN Container Configurations

This folder contains two Docker Compose configurations for Gluetun, a containerized VPN client. I use Gluetun in my homelab to:

1. Securely tunnel traffic between my Hetzner-hosted Docker services and my home network via WireGuard
2. Route selected containers' internet traffic through ProtonVPN for privacy

---

## 🛠️ Use Case 1: Site-to-Site VPN Tunnel (Hetzner → Home Network)

**Goal:**  
Enable services running in the cloud (Hetzner) to communicate securely with my home LAN.

### Key Components:
- **WireGuard Server:** Hosted on home router (Ubiquiti Dream Machine Pro in my case)
- **Gluetun Client:** Running in Docker in the cloud
- **Docker Network (Cloud):** `192.168.19.0/24`
- **Home LAN:** `192.168.0.0/24`
- **VPN Tunnel Subnet:** `10.1.1.0/24`

### Routing Notes:
- DNAT on UDM Pro redirects traffic destined to cloud Docker network to Gluetun (`10.1.1.2`) for Docker subnet access
- Custom `iptables` post-rule file added to Gluetun to accept incoming connections from the home LAN

### Files:
- `docker-compose.home.yml`
- `/iptables/post-rules.txt` — Custom iptables rule

---

## 🔒 Use Case 2: Container Traffic via ProtonVPN

**Goal:**  
Route selected Docker containers' outbound traffic through ProtonVPN, ensuring privacy and IP masking.

### Features:
- Containers joined to Gluetun's Docker network
- Kill-switch behavior: if VPN drops, traffic is blocked

### Files:
- `docker-compose.protonvpn.yml`

---

## 🔧 How to Use

### 1. Clone the repo and navigate to this folder:
```bash
git clone https://github.com/logand99/homelab.git
cd gluetun
```
### 2. Modify environment variables as needed (e.g. WireGuard config or ProtonVPN credentials)
### 3. Start the container
```bash
# For WireGuard Tunnel
docker-compose -f docker-compose.home.yml up -d

# For ProtonVPN Tunnel
docker-compose -f docker-compose.protonvpn.yml up -d

