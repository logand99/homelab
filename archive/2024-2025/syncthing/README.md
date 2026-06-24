# Syncthing Docker Configuration

This folder contains my Docker Compose setup for running Syncthing on a Raspberry Pi. I use Syncthing to synchronize game save files between devices — creating a self-hosted "cloud save" system for games that don't support native cloud syncing.

---

## 🎮 Use Case: Game Save Synchronization

I use Syncthing to keep game save files synced between:
- **Gaming PC** (Windows)
- **Gaming PC** (Linux)
- **Steam Deck** (Linux)

The sync server runs on a **Raspberry Pi 5** using Docker and Portainer. Game saves are stored on a mounted **TrueNAS SMB share**, which provides persistent storage and daily cloud backups.

---

## 🧱 Deployment Details

- **Host Device:** Raspberry Pi 5
- **Platform:** Docker (managed via Portainer)
- **Storage Location:** Mounted SMB share from TrueNAS
- **Synced Folder:** Game saves directory, mapped into the container as a persistent volume

---

## 📦 Files Included

| Filename            | Description                                 |
|---------------------|---------------------------------------------|
| `docker-compose.yml`| Deploys the Syncthing container             |
| `README.md`         | This documentation file                     |

---

## ⚙️ How to Use

### 1. Clone the Repo
```bash
git clone https://github.com/logand99/homelab.git
cd syncthing
```
### 2. Start the Container
```bash
docker-compose up -d
```
