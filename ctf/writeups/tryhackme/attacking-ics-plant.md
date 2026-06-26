---
layout: page
title: Attacking ICS Plant - TryHackMe Writeup
subtitle: Industrial Control Systems (ICS/SCADA) exploitation, Modbus protocol abuse, and HMI takeover.
permalink: /ctf/writeups/tryhackme/attacking-ics-plant/
platform: tryhackme
machine_name: attacking-ics-plant
difficulty: Hard
os: Web
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: tryhackme
* **Name / Title**: attacking-ics-plant
* **Difficulty**: Hard
* **Target OS / Environment**: Web
* **Key Vulnerability Focus**: SCADA / Modbus protocol abuse

---

### ICS Attack Vector

1. **Reconnaissance**: Scanning for industrial ports (e.g. port 502 for Modbus).
2. **HMI Takeover**: Exploiting default passwords on the Human-Machine Interface (HMI) web control panel.
3. **Modbus Protocol Abuse**: Sending direct Modbus write commands to alter PLC registers, simulating physical control overrides.
