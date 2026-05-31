# 🛡️ Sentinel Ops Bot

A custom Discord operations bot for **homelab health monitoring, alerting, and incident visibility**.

The Sentinel Ops Bot was built to turn infrastructure health data into actionable Discord alerts, giving a lightweight operational interface for monitoring system performance, service failures, container health, network quality, and OpenClaw-related issues from a central channel.

---

## 📌 Project Summary

This project acts as an alerting and notification layer for a self-hosted environment. It reads generated health snapshots, evaluates them against defined thresholds, tracks alert state, and posts only meaningful operational events to Discord.

Instead of dumping raw metrics into chat, the bot focuses on **signal over noise** by:

- identifying warning and critical conditions
- suppressing repetitive alert spam
- escalating long-lived issues
- notifying on recovery when conditions clear
- mentioning the configured operator on critical incidents

From a resume and portfolio perspective, this project highlights experience in:

- infrastructure monitoring and alerting
- operational tooling design
- Discord bot development
- threshold-based incident detection
- Linux and service health awareness
- stateful notification workflows
- homelab observability and automation

---

## 🎯 Objectives

The Sentinel Ops Bot was designed to solve a common homelab problem: important infrastructure issues can be easy to miss without a simple, centralized alerting workflow.

### Goals

- Provide near-real-time Discord visibility into homelab health
- Surface actionable incidents instead of raw telemetry noise
- Track alert state so repeated failures do not spam the channel
- Send recovery messages when issues clear
- Create a reusable monitoring pattern that can grow over time

---

## 🧱 Architecture Overview

The bot runs locally and works as the notification layer for Sentinel collector output.

### High-level flow

1. A collector process generates a health snapshot as JSON
2. The bot reads the latest status file from disk
3. Current values are compared to configured warning and critical thresholds
4. The bot reconciles current issues against saved alert state
5. New incidents, severity changes, and recoveries are posted to Discord
6. Alert state is persisted locally to prevent repeated spam

This design separates data collection from alert delivery, which makes the overall monitoring workflow easier to maintain and extend.

---

## ⚙️ What It Monitors

The Sentinel Ops Bot evaluates multiple categories of homelab health:

### System resource pressure

- CPU utilization
- RAM usage
- Disk utilization

### Network quality

- packet loss
- elevated latency
- degraded download bandwidth samples

### Service and container health

- failed systemd units
- unhealthy Docker containers

### OpenClaw-related health and security

- OpenClaw health check failures
- critical findings from OpenClaw security audit summaries

This gives the bot value as a practical operations monitor rather than a single-purpose notifier.

---

## 🚨 Alerting Model

A key strength of the project is its stateful alerting behavior.

### Alert behavior

- classifies conditions as warning or critical
- sends immediate notifications for new issues
- escalates when severity changes
- avoids repeated spam for the same unresolved condition
- sends recovery messages when a condition has remained clear long enough
- optionally mentions the configured operator on critical incidents

This is a much stronger operational pattern than simply posting every failed check on a timer.

---

## 🔐 Operational Design Considerations

The project was built with practical operational discipline in mind.

### Design choices

- Uses a dedicated status file as the system input instead of tying monitoring directly to Discord commands
- Persists alert state locally so the bot can reason about changes over time
- Keeps notification logic separate from data collection logic
- Uses threshold-driven classification for clearer operational decisions
- Prioritizes low-noise incident visibility over constant metric reporting

This reflects real-world thinking around observability, reliability, and operator experience.

---

## 🛠️ Deployment Approach

The Sentinel Ops Bot is designed for always-on use in a Linux homelab environment.

### Deployment workflow

- configure bot authentication and Discord channel settings
- generate or refresh system health snapshots through a collector pipeline
- run the bot as a persistent process
- schedule collector updates at a fixed interval

### Runtime behavior

The bot reads:

- a generated Sentinel status file
- a local JSON state file for alert history and reconciliation

It then posts only the events that matter, which keeps the operations channel readable and useful.

---

## 🧠 Technical Skills Demonstrated

This project showcases practical experience in areas that transfer well to IT, systems, and operations roles:

- **Discord bot development** for operational workflows
- **Stateful alerting logic** for incident tracking and recovery handling
- **JSON-based monitoring pipelines** for metric ingestion and processing
- **Linux systems awareness** including systemd and disk/resource health
- **Container operations awareness** through Docker health monitoring
- **Network troubleshooting signals** such as packet loss, latency, and bandwidth degradation
- **Infrastructure observability design** focused on clarity and operator usefulness

---

## 💼 Resume Value

This project is strong resume material because it demonstrates more than “I made a monitoring bot.”

It shows the ability to:

- identify monitoring and visibility gaps in a live environment
- design a custom tool around operational needs
- build alerting logic that balances sensitivity with noise reduction
- integrate infrastructure health signals into a usable workflow
- think in terms of incidents, state, recovery, and operator response

That maps well to roles involving:

- IT operations
- systems administration
- junior DevOps or SRE-adjacent work
- infrastructure support
- internal tooling and automation

---

## 🔮 Future Expansion

This project can be extended in several directions:

- slash commands for live status, acknowledgements, silencing, or summaries
- richer Discord embeds for incident formatting
- incident threading or message updates instead of separate posts
- summary/digest reporting for lower-priority warnings
- per-service or per-host alert routing
- dashboard integration for historical trend visibility

Those improvements would push the bot even further toward a fuller internal operations platform.

---

## 🔗 Repository Context

This project is part of the broader **GreedOS Homelab** repository and represents a custom-built monitoring and alerting tool developed for real-world self-hosted infrastructure.

It reflects practical experience in observability, automation, incident visibility, and building internal tools that improve the day-to-day usability of a homelab environment.
