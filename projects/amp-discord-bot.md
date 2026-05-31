# 🤖 AMP Discord Bot

A custom Discord operations bot for managing **AMP-hosted game server instances** through a secure, role-restricted chat interface.

This project demonstrates how Discord can be used as a lightweight operational layer for self-hosted infrastructure, allowing trusted users to perform controlled server actions and receive status updates without requiring direct host or panel access.

---

## 📌 Project Summary

The AMP Discord Bot was designed to simplify administrative workflows for self-hosted game servers by connecting **Discord slash commands** to **local AMP instance management**.

Instead of logging into the host or AMP web interface for routine tasks, authorized users can manage server lifecycle actions directly from Discord. The bot also supports status monitoring and state-change notifications, making it useful as both a control surface and an operational awareness tool.

From a resume and portfolio perspective, this project highlights experience in:

- infrastructure automation
- secure administrative tooling
- API-driven service management
- Discord bot development
- Linux service deployment and supervision
- operational access control for self-hosted systems

---

## 🎯 Objectives

This project was built to solve a practical homelab problem: reducing friction around day-to-day game server administration while keeping management actions secure and auditable.

### Goals

- Provide a simple chat-based interface for server administration
- Reduce the need for direct host or panel logins for routine tasks
- Restrict administrative actions to trusted Discord users, roles, or channels
- Surface server state changes in a low-noise, operationally useful way
- Build a reusable control pattern that can extend beyond a single game server

---

## 🧱 Architecture Overview

The bot runs locally on the same machine that can already manage AMP and the associated game server instances.

### High-level flow

1. A trusted user issues a Discord slash command
2. The bot validates access permissions
3. The bot authenticates against AMP locally
4. The bot targets the appropriate managed instance
5. The requested lifecycle action or status check is performed
6. The result is returned to Discord

This architecture keeps the control path local and minimizes unnecessary external exposure while still providing a convenient administrative interface.

---

## ⚙️ Key Capabilities

### Discord-based server operations

The bot exposes slash-command driven workflows for common instance-management tasks such as:

- starting a server
- stopping a server
- restarting a server
- checking current server status

### AMP-centered control layer

Rather than being tightly coupled to one game title, the project is framed around **AMP as the management platform**, which makes the approach more reusable and transferable.

### Access control and operational safety

Administrative actions can be restricted using configuration such as:

- `ALLOWED_USER_IDS`
- `ALLOWED_ROLE_IDS`
- `ALLOWED_CHANNEL_IDS`

This allows the bot to function as a controlled operational tool instead of an open server command interface.

### State-change notifications

A built-in watcher can poll local state and send updates only when the instance status changes.

This supports low-noise alerting patterns such as:

- server came online
- server stopped
- instance changed from idle to running

By avoiding repetitive status spam, the bot stays useful in a real Discord environment.

---

## 🔐 Security and Design Considerations

A major design goal was balancing convenience with operational safety.

### Security-minded decisions

- Runs locally on infrastructure that already has authority to manage AMP
- Limits command access to explicitly allowed users, roles, or channels
- Avoids exposing direct infrastructure access to casual users
- Uses Discord as a thin control interface, not as the system of record
- Supports a cleaner separation between user interaction and privileged local actions

This demonstrates practical thinking around least privilege, administrative boundaries, and safe automation patterns in self-hosted environments.

---

## 🛠️ Deployment Approach

The bot is intended for always-on operation in a Linux homelab environment.

### Deployment workflow

- configure environment variables for Discord and AMP access
- install dependencies with Node.js/npm
- register Discord slash commands
- run the bot as a background service

### Service management

The project supports deployment as a **systemd user service**, which improves reliability and maintainability by enabling:

- automatic service startup
- centralized log inspection
- predictable restart behavior
- simpler long-running process management

This is the kind of small but important operational detail that separates a quick script from a more production-minded internal tool.

---

## 🧠 Technical Skills Demonstrated

This project showcases practical experience across several areas relevant to IT, systems administration, and infrastructure roles:

- **Discord API integration** for slash-command based workflows
- **Node.js application development** for automation tooling
- **AMP instance management** and panel-driven service orchestration
- **Linux operations** including process/service management with systemd
- **Access control design** for administrative tooling
- **Operational monitoring patterns** using state-based notifications
- **Homelab automation** focused on reducing repetitive infrastructure tasks

---

## 💼 Resume Value

This project is useful as a portfolio example because it demonstrates more than just "I built a bot."

It shows the ability to:

- identify an operational pain point
- design a practical internal tool to solve it
- integrate multiple systems into one workflow
- apply security restrictions to administrative actions
- deploy and maintain the tool in a real self-hosted environment

That combination maps well to roles involving:

- IT support and systems administration
- infrastructure operations
- platform/tooling support
- junior DevOps or automation work
- technical operations in self-hosted or small-team environments

---

## 🔮 Future Expansion

The design can be extended in several useful directions:

- support for multiple AMP-managed game servers
- richer status reporting such as uptime, player counts, or resource usage
- structured Discord embeds for cleaner operational output
- audit logging for administrative actions
- confirmation or maintenance workflows for disruptive actions
- automated recovery or health-check logic for failed starts

These next steps would further strengthen the project as an example of operational tooling and service automation.

---

## 🔗 Repository Context

This project is part of the broader **GreedOS Homelab** repository and represents a custom-built internal operations tool developed within a self-hosted infrastructure environment.

It reflects a practical, real-world approach to improving infrastructure usability through automation, controlled access, and lightweight service management.
