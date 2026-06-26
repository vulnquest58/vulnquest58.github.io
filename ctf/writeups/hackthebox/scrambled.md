---
layout: page
title: Scrambled - Hack The Box Writeup
subtitle: Silver Ticket Attack against Windows Server IIS Service and Net Deserialization
permalink: /ctf/writeups/hackthebox/scrambled/
platform: hackthebox
machine_name: scrambled
difficulty: Hard
os: Windows
date: 2026-06-26
---

## ðŸ–¥ï¸ Challenge / Machine Info
* **Platform**: hackthebox
* **Name / Title**: scrambled
* **Difficulty**: Hard
* **Target OS / Environment**: Windows
* **Key Vulnerability Focus**: Kerberos Silver Ticket / .NET Deserialization

---

### Exploitation Flow

1. **Reconnaissance**: AD forest running Kerberos authentication.
2. **Silver Ticket Attack**: We request a TGS ticket for the IIS SPN, extract the NTLM hash of the service account, and craft a Silver Ticket (forged Kerberos TGS) granting us administrator privileges on the IIS server.
3. **Privilege Escalation**: The web app deserializes user cookies. We generate a custom YsoSerial.net binary payload to trigger command execution on deserialization, giving us local SYSTEM access.
