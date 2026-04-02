# 🎮 Palworld Discord Bot

A lightweight Discord slash-command bot for managing an AMP-hosted **Palworld** dedicated server from Discord.

This project was built to give trusted users a simple way to start, stop, restart, and check the status of the Palworld server without logging directly into the host.

---

## 🚀 Overview

The bot runs locally on the same machine that manages the Palworld server and AMP instance. It connects Discord interactions to local server-management actions and can also post status-change notifications automatically.

### Core functions

- Start the Palworld server from Discord
- Stop the Palworld server from Discord
- Restart the Palworld server from Discord
- Check server status from Discord
- Watch the server state and post updates only when it changes

---

## ⚙️ How It Works

The bot uses **Discord slash commands** as the user interface and performs local checks/actions against the Palworld environment.

### Command interface

Supported commands:

- `/palworld start`
- `/palworld status`
- `/palworld stop`
- `/palworld restart`

### Local control path

The bot is designed to run on the host that can already manage the game server locally. It relies on:

- **AMP** for instance management
- **Docker/process checks** for secondary status validation
- A local helper flow that:
  - logs into AMP locally
  - requests a remote-instance management token
  - logs into the Palworld instance through AMP's ADS flow
  - performs start/stop/restart/status actions against the managed instance

This keeps the operational control local while exposing only a clean Discord interface to allowed users.

---

## 🔐 Access Control

The bot is intentionally restricted so not everyone in a Discord server can control infrastructure.

By default, command use is limited to the Discord user IDs listed in:

- `ALLOWED_USER_IDS`

Optional additional restrictions:

- `ALLOWED_ROLE_IDS` — allow listed Discord roles
- `ALLOWED_CHANNEL_IDS` — restrict commands to specific channels

This makes it possible to keep server controls limited to trusted admins or a dedicated ops channel.

---

## 📣 Built-in Watcher

The project includes a watcher that can periodically poll the local Palworld/AMP state and post updates only when the state changes.

Example watcher settings:

- `NOTIFY_CHANNEL_ID`
- `WATCHER_ENABLED=true`
- `WATCH_INTERVAL_MS=60000`

### Watcher behavior

- Polls locally on an interval
- Uses AMP and local Docker/process checks
- Posts only on state transitions
- Avoids noisy repeat messages when nothing changes

Example transitions:

- `idle -> running`
- `running -> idle`

This makes it useful for lightweight operational awareness without turning Discord into log spam.

---

## 🧱 Host Requirements

The bot must run on the same machine that can directly manage the Palworld instance.

Expected local environment:

- Docker access on the host
- AMP panel reachable locally
- Palworld instance configured in AMP

Current target assumptions used by the project:

- Docker container: `AMP_Palworld01`
- AMP instance: `Palworld01`
- AMP local panel: `http://127.0.0.1:8089`

AMP-related environment variables include:

- `AMP_BASE_URL`
- `AMP_USERNAME`
- `AMP_PASSWORD`
- `AMP_INSTANCE_ID`

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

1. Copy `palworld-discord-bot.service` into `~/.config/systemd/user/`
2. Run `systemctl --user daemon-reload`
3. Run `systemctl --user enable --now palworld-discord-bot.service`
4. Monitor logs with `journalctl --user -u palworld-discord-bot.service -f`

---

## 🧠 Why This Project Matters

This project is a good example of practical homelab automation because it connects several real-world concerns:

- Discord bot development
- Role-based operational access
- Game server lifecycle management
- AMP integration
- Service supervision with systemd
- Low-noise operational notifications

It reflects the kind of tooling that grows naturally in a self-hosted environment: small, focused automation that solves a real operational pain point.

---

## 🔮 Future Improvements

Potential next steps for the project:

- Add richer status output (player count, uptime, world info)
- Add structured embeds for status and alerts
- Add command/audit logging for admin actions
- Add maintenance mode or confirmation flows for destructive actions
- Add health checks for failed startups
- Expand to manage additional game servers through the same pattern

---

## 🔗 Repository Context

This bot is part of the broader **GreedOS Homelab** ecosystem and documents a custom operational tool built around self-hosted infrastructure and Discord-based server administration.
