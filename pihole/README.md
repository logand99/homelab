# Pi-hole Docker Configurations

This folder contains the Docker Compose configurations used for my distributed Pi-hole deployment and the supporting configuration for [nebula-sync](https://github.com/lovelaze/nebula-sync).

Pi-hole serves as the primary DNS platform for my homelab, providing network-wide ad blocking, local DNS services, and internal service discovery.

---

## Overview

My DNS infrastructure consists of three Pi-hole instances distributed across separate systems to provide redundancy and eliminate single points of failure.

| Host       | Platform             | Deployment Type | Role      |
| ---------- | -------------------- | --------------- | --------- |
| Hermes     | Raspberry Pi 4 (8GB) | Bare Metal      | Primary   |
| Thalia     | Raspberry Pi 5 (8GB) | Docker          | Secondary |
| Euphrosyne | Raspberry Pi 5 (8GB) | Docker          | Tertiary  |

All instances share the same configuration through Nebula Sync, ensuring consistent DNS records, blocklists, allowlists, and settings.

> **Note:** The primary Pi-hole instance (Hermes) is deployed directly on Raspberry Pi OS and therefore does not have a Docker Compose configuration included in this repository.

---

## Repository Contents

### Thalia Pi-hole

**Compose File:** `docker-compose.thalia.yml`

Runs Pi-hole as a Docker container on the Thalia Raspberry Pi 5 node.

### Euphrosyne Pi-hole

**Compose File:** `docker-compose.euphrosyne.yml`

Runs Pi-hole as a Docker container on the Euphrosyne Raspberry Pi 5 node.

### Nebula Sync

**Compose File:** `docker-compose.nebula-sync.yml`

Automatically synchronizes:

* Local DNS records
* Allowlists
* Blocklists
* Groups
* DNS settings

Across all Pi-hole instances.

---

## DNS Architecture

Pi-hole is used for both DNS filtering and local service discovery throughout my homelab.

Internal services are accessed through the following namespace:

```text
home.logand99.com
```

Examples:

```text
portainer.home.logand99.com
bookstack.home.logand99.com
photoprism.home.logand99.com
guacamole.home.logand99.com
```

This allows services to be accessed using friendly hostnames rather than IP addresses.

---

## Upstream DNS

All Pi-hole instances use Cloudflare DNS as their upstream resolver.

```text
1.1.1.1
1.0.0.1
```

---

## Features

* Network-wide ad blocking
* Tracker and telemetry filtering
* Malware and phishing protection
* Local DNS record management
* Redundant DNS infrastructure
* Automated configuration synchronization
* Docker-based deployment

---

## Deploying a Pi-hole Instance

Clone the repository:

```bash
git clone https://github.com/logand99/homelab.git
cd homelab/pihole
```

Deploy a Pi-hole instance:

```bash
docker compose -f docker-compose.thalia.yml up -d
```

or

```bash
docker compose -f docker-compose.euphrosyne.yml up -d
```

Deploy Nebula Sync:

```bash
docker compose -f docker-compose.nebula-sync.yml up -d
```

---

## Technologies Used

* Pi-hole
* Docker
* Docker Compose
* Nebula Sync
* Raspberry Pi 4
* Raspberry Pi 5
* Cloudflare DNS
* Linux
