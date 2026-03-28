# 🖥️ GreedOS Homelab

A self-hosted homelab environment built to design, deploy, and manage real-world infrastructure using Linux, Docker, and networked storage.

This project documents my hands-on experience building a scalable home server ecosystem focused on media streaming, automation, monitoring, and secure remote access.

---

## 🚀 Overview

GreedOS is a multi-device homelab that integrates compute, storage, and networking into a cohesive system. It serves as both a personal platform and a learning environment for system administration, networking, and infrastructure design.

---

## 🧱 Infrastructure

### 💻 Compute

* Lenovo ThinkCentre M710q (Ubuntu Server)

  * Hosts Docker containers and core services
* Raspberry Pi 5

  * Runs Home Assistant for smart home automation

### 💾 Storage

* Synology DS923+

  * Centralized NAS for media, backups, and persistent data
* Network-mounted storage:

  * `/mnt/media` (NFS share)

### 🌐 Networking

* Netgear Nighthawk R8000
* Cloudflare Tunnels (secure public access)
* Tailscale VPN (private remote access)

---

## 📦 Services

All services are containerized using Docker Compose for portability and scalability.

### 🎬 Media Stack

* Plex (media server with hardware transcoding)
* Sonarr / Radarr (media automation)
* Seerr (request automation)
* Prowlarr (index management)
* qBittorrent + Gluetun (VPN-protected downloads)

### 📸 Self-Hosted Apps

* Immich (photo and video backup)
* Frigate + go2rtc (NVR and camera monitoring)
* Home Assistant (smart home control)

### 📊 Monitoring & Tools *(in progress)*

* Netdata / Grafana (system monitoring)
* Homepage dashboard (service overview)

---

## ⚙️ Key Features

* **Dockerized architecture** for easy deployment and management
* **Intel Quick Sync (QSV)** for hardware-accelerated media processing
* **Centralized NAS storage** shared across services
* **Secure remote access** using Cloudflare Zero Trust and VPN
* **Service isolation and modular design** for scalability

---

## 🧠 What I Learned

* Managing Linux servers and system services
* Designing and troubleshooting Docker-based environments
* Networking fundamentals (routing, remote access, segmentation)
* Debugging real-world issues (permissions, mounts, port conflicts)
* Building reliable, always-on infrastructure

---

## 🔧 Challenges & Solutions

| Challenge                           | Solution                                                 |
| ----------------------------------- | -------------------------------------------------------- |
| NAS struggled with Plex transcoding | Migrated Plex to dedicated Ubuntu server with Quick Sync |
| Docker permission errors (EACCES)   | Standardized PUID/PGID and volume ownership              |
| Port conflicts across services      | Re-mapped container ports and documented usage           |
| Remote access complexity            | Implemented Cloudflare Tunnels + Tailscale               |

---

## 🚧 Roadmap

* [ ] Implement VLAN segmentation for IoT and services
* [ ] Deploy Authentik for SSO authentication
* [ ] Expand monitoring with Grafana dashboards
* [ ] Add automated backups and alerting
* [ ] Improve network infrastructure (PoE + access points)

---

## 📸 Screenshots


---

## 🔗 Related Projects


---

## 👤 Author

**Brandon Daugherty**
IT Technician | Homelab Enthusiast

* GitHub: https://github.com/brandondaugherty

---

## 💬 Purpose

This repository is part of my ongoing effort to transition into more advanced IT, infrastructure, and potentially cybersecurity-focused roles by documenting real-world, hands-on projects.

---

