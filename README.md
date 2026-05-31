# GreedOS Homelab

A self-hosted homelab built to develop hands-on experience in **Linux administration, infrastructure operations, networking, monitoring, storage, and service automation**.

This repository documents the systems, tooling, and operational decisions behind my home infrastructure. My goal is to use it as both a working environment and a professional portfolio for **systems administration and infrastructure-focused roles**.

## Professional Focus

GreedOS is designed to reflect the kinds of responsibilities involved in real sysadmin work:

- provisioning and maintaining Linux-based systems
- deploying and operating containerized services
- managing storage and shared mounts across applications
- implementing secure remote access patterns
- monitoring service health and host performance
- troubleshooting permissions, networking, and service failures
- building internal tooling to improve operations
- documenting infrastructure clearly enough for repeatability and handoff

## Environment Overview

### Compute

- **Lenovo ThinkCentre M710q** running Ubuntu Server
- **Raspberry Pi 5** supporting Home Assistant and smart home automation

### Storage

- **Synology DS923+** for centralized NAS storage, media, backups, and persistent data
- network-mounted storage exposed to services through shared paths such as `/mnt/media`

### Networking and Access

- **Netgear Nighthawk R8000**
- **Cloudflare Tunnels** for controlled public access to selected services
- **Tailscale VPN** for private remote administration and access

## Core Technologies and Responsibilities

This homelab reflects ongoing hands-on work with:

- **Ubuntu Server / Linux administration**
- **Docker and Docker Compose**
- **systemd services and service supervision**
- **network storage and mount management**
- **remote access and secure exposure patterns**
- **service monitoring and operational alerting**
- **container troubleshooting and host-level debugging**
- **documentation and infrastructure organization**

## Service Stack

### Media and Content Services

- Plex
- Sonarr
- Radarr
- Prowlarr
- Seerr
- qBittorrent + Gluetun

### Self-Hosted Infrastructure and Apps

- Home Assistant
- Immich
- Frigate + go2rtc
- Homepage dashboard

### Monitoring and Operations

- Netdata / Grafana
- internal Discord-based ops tooling
- health and status monitoring workflows

## Operational Projects in This Repository

These project write-ups show the kind of tooling and operational thinking I’ve been building around the homelab.

- [AMP Discord Bot](projects/amp-discord-bot.md)  
  Discord-based administrative tooling for AMP-hosted game server management, including role-restricted operations and low-noise status notifications.

- [Sentinel Ops Bot](projects/sentinel-ops-bot.md)  
  Discord-based monitoring and alerting for homelab health, incident visibility, Docker/systemd issues, network quality, and OpenClaw-related signals.

## Key Sysadmin Themes Demonstrated

### Linux and Service Operations

This environment gives me regular practice with:

- service deployment and lifecycle management
- systemd-based process supervision
- host troubleshooting and log inspection
- resource monitoring and capacity awareness
- disk, memory, and CPU usage analysis

### Container and Application Management

I use Dockerized services heavily, which has required hands-on work with:

- Compose-based service definitions
- volume and permission management
- service isolation and inter-service dependencies
- port conflicts and application exposure
- persistent storage planning

### Monitoring, Alerting, and Reliability

A major part of the homelab is operational visibility. That includes:

- identifying failed services and unhealthy containers
- building low-noise alerting instead of raw metric spam
- monitoring host and network conditions
- creating internal tooling for faster incident awareness

### Security and Remote Access

This environment also reflects practical exposure to:

- private remote access with VPN
- selective public exposure through tunnels
- minimizing unnecessary external surface area
- thinking about administrative boundaries and access control

## Selected Challenges and What They Taught Me

| Challenge | What I Learned / Implemented |
| --- | --- |
| NAS limitations under media workloads | Moved heavier media responsibilities to a dedicated Ubuntu host and improved workload placement |
| Docker permission issues | Standardized volume ownership and improved consistency around service access |
| Port conflicts between self-hosted services | Reworked service mappings and improved documentation of port usage |
| Remote access complexity | Combined private VPN access with controlled tunnel-based exposure |
| Monitoring gaps | Built custom internal tooling to surface health issues in a more operationally useful way |

## Why This Repository Exists

This repo is meant to do more than list what I run at home. It is intended to show how I think about:

- building and maintaining infrastructure
- documenting systems clearly
- improving reliability and visibility
- solving operational problems with automation
- growing from hands-on IT support into stronger systems administration work

## Roadmap

Planned improvements include:

- VLAN segmentation for service and IoT isolation
- stronger identity and access management patterns
- expanded monitoring and dashboarding
- better backup and alerting coverage
- continued cleanup and documentation of service architecture

## About Me

**Brandon Daugherty**  
IT Technician | Homelab Enthusiast | Infrastructure, Networking, and Automation

GitHub: <https://github.com/brandondaugherty>

---

If you are reviewing this repository professionally, the most relevant sections are the project pages and the operational themes above. They best reflect the sysadmin-oriented work this homelab is helping me build experience in.
