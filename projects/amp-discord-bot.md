# 🤖 AMP Discord Bot

A lightweight Discord slash-command bot for managing **AMP-hosted game server instances** from Discord.

This project was built to give trusted users a simple way to start, stop, restart, and check the status of an AMP-managed server without logging directly into the host.

---

## 🚀 Overview

The bot runs locally on the same machine that hosts the AMP panel and manages one or more game server instances. It connects Discord interactions to local AMP-driven server-management actions and can also post status-change notifications automatically.

### Core functions

- Start an AMP-managed server from Discord
- Stop an AMP-managed server from Discord
- Restart an AMP-managed server from Discord
- Check server status from Discord
- Watch server state and post updates only when it changes

---

## ⚙️ How It Works

The bot uses **Discord slash commands** as the user interface and performs local checks and actions against an AMP-managed environment.

### Command interface

The current implementation exposes Discord slash commands for instance control and status checks. While the first use case centered on a specific game server, the overall pattern is built around AMP as the control layer rather than any single title.

### Local control path

The bot is designed to run on the same host that can already manage AMP locally. It relies on:

- **AMP** for instance management
- **Local Docker/process checks** for secondary status validation
- A local helper flow that:
  - logs into AMP locally
  - requests a remote-instance management token
  - logs into the target managed instance through AMP's ADS flow
  - performs start/stop/restart/status actions against the selected instance

This keeps operational control local while exposing only a clean Discord interface to allowed users.

---

## 🔐 Access Control

The bot is intentionally restricted so not everyone in a Discord server can control infrastructure.

By default, command use is limited to the Discord user IDs listed in:

- `ALLOWED_USER_IDS`

Optional additional restrictions:

- `ALLOWED_ROLE_IDS` — allow listed Discord roles
- `ALLOWED_CHANNEL_IDS` — restrict commands to specific channels

This makes it possible to keep administrative controls limited to trusted users or a dedicated operations channel.

---

## 📣 Built-in Watcher

The project includes a watcher that can periodically poll AMP and local service state, then post updates only when the state changes.

Example watcher settings:

- `NOTIFY_CHANNEL_ID`
- `WATCHER_ENABLED=true`
- `WATCH_INTERVAL_MS=60000`

### Watcher behavior

- Polls locally on a fixed interval
- Uses AMP and local Docker/process checks
- Posts only on state transitions
- Avoids noisy repeat messages when nothing changes

Example transitions:

- `idle -> running`
- `running -> idle`

This makes it useful for lightweight operational awareness without turning Discord into a noisy log feed.

---

## 🧱 Host Requirements

The bot must run on the same machine that can directly manage AMP instances.

Expected local environment:

- Docker access on the host when container-based checks are used
- AMP panel reachable locally
- One or more server instances configured in AMP

Typical AMP-related environment variables include:

- `AMP_BASE_URL`
- `AMP_USERNAME`
- `AMP_PASSWORD`
- `AMP_INSTANCE_ID`

The original deployment targeted a specific game server instance, but the documentation now reflects the broader AMP-centered architecture and control pattern.

---

## 🛠️ Deployment Notes

Basic setup flow:

1. Copy `.env.example` to `.env`
2. Add Discord bot credentials and AMP credentials
3. Install dependencies with `npm install`
4. Register slash commands with `npm run register`
5. Start the bot with `npm start`

The bot can also be run as a **systemd user service**, which makes it practical for always-on homelab operation.

Example service workflow:

1. Copy the provided service file into `~/.config/systemd/user/`
2. Run `systemctl --user daemon-reload`
3. Run `systemctl --user enable --now <service-name>`
4. Monitor logs with `journalctl --user -u <service-name> -f`

---

## 🧠 Why This Project Matters

This project is a strong example of practical homelab automation because it connects several real-world concerns:

- Discord bot development
- Role-based operational access
- AMP instance lifecycle management
- Local service supervision
- Systemd-based background operation
- Low-noise operational notifications

It reflects the kind of tooling that grows naturally in a self-hosted environment: small, focused automation that solves a real operational pain point.

---

## 🔮 Future Improvements

Potential next steps for the project:

- Support multiple AMP-managed game servers through a shared command structure
- Add richer status output such as player counts, uptime, and resource use
- Add structured embeds for status and alerts
- Add command and audit logging for admin actions
- Add maintenance mode or confirmation flows for destructive actions
- Add health checks and recovery handling for failed startups

---

## 🔗 Repository Context

This bot is part of the broader **GreedOS Homelab** ecosystem and documents a custom operational tool built around self-hosted infrastructure and Discord-based administration for AMP-managed services.
