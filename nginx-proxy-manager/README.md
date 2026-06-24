# Nginx Proxy Manager (NPM) Docker Configuration

This folder contains the Docker Compose configuration for my Nginx Proxy Manager (NPM) deployment.

NPM serves as the internal reverse proxy for my homelab, providing centralized service routing and HTTPS access to self-hosted applications running across multiple Raspberry Pi systems.

---

## Overview

Nginx Proxy Manager is used to:

* Route traffic to internal services
* Provide friendly DNS-based URLs
* Simplify reverse proxy management
* Centralize application access
* Manage internal HTTPS certificates

Rather than accessing services by IP address and port, applications can be reached using hostnames such as:

```text
portainer.home.logand99.com
bookstack.home.logand99.com
photoprism.home.logand99.com
guacamole.home.logand99.com
```

---

## Current Deployment

### Home Network Instance

* **Compose File:** `docker-compose.yml`
* **Hosted On:** Raspberry Pi 5
* **Deployment Method:** Docker via Portainer
* **Purpose:** Internal reverse proxy and service routing

This is currently the only Nginx Proxy Manager instance in my environment.

---

## Architecture

Traffic flows through the homelab as follows:

```text
Client Device
      ↓
Pi-hole DNS
      ↓
Nginx Proxy Manager
      ↓
Target Service
```

Pi-hole provides local DNS resolution while NPM handles reverse proxying and routing requests to the appropriate service.

---

## Cloudflare Integration

External access to selected services is handled through Cloudflare Tunnel.

Cloudflare provides:

* Public DNS
* TLS termination
* Secure remote access
* Protection from exposing inbound ports

NPM remains responsible for internal service routing after traffic reaches the homelab.

---

## Features

* Internal reverse proxy management
* Service routing by hostname
* Centralized application access
* Docker-based deployment
* Integration with Pi-hole DNS
* Integration with Cloudflare Tunnel

---

## Deploying

Clone the repository:

```bash
git clone https://github.com/logand99/homelab.git
cd nginx-proxy-manager
```

Start Nginx Proxy Manager:

```bash
docker compose up -d
```

---

## Security Notes

* No inbound ports are exposed directly to the internet for remote access.
* External access is provided through Cloudflare Tunnel.
* Internal services are accessed through DNS-based routing.
* Administrative access is restricted to trusted networks and authenticated users.

---

## Technologies Used

* Nginx Proxy Manager
* Docker
* Docker Compose
* Portainer
* Pi-hole
* Cloudflare Tunnel
* Cloudflare DNS
* Raspberry Pi 5
* Linux
