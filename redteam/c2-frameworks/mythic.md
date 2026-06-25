---
layout: page
title: Mythic C2 Configuration
subtitle: Containerized multi-platform C2 framework
permalink: /redteam/c2-frameworks/mythic/
---

## Mythic C2 Framework

Mythic is a containerized, collaborative red team framework developed by its-a-feature. It uses Docker to run each component (server, database, agents, and communication profiles) independently, making it highly modular and extensible.

### Architecture Overview

Mythic consists of several Docker containers working together:
- **Mythic Server**: Main API server and operator web console (port 7443).
- **PostgreSQL**: Persistent database for operation data and task logs.
- **RabbitMQ**: Message broker between the Mythic server and C2 profile containers.
- **Agent Containers**: Separate containers building and serving compiled agents.
- **C2 Profile Containers**: Independent transport handlers (HTTP, HTTPS, SMB, etc.).

### Installation

```bash
git clone https://github.com/its-a-feature/Mythic
cd Mythic
./mythic-cli install github https://github.com/MythicAgents/Apollo
./mythic-cli install github https://github.com/MythicC2Profiles/http
./mythic-cli start
```

Access the console at `https://localhost:7443`.

---

## Agents & Profiles

### Apollo (Windows .NET Agent)
Apollo is a Windows-focused agent written in C#. It supports:
- **Indirect Syscalls**: Dynamically resolves system calls at runtime to bypass EDR hooks on NTDLL.
- **Token Manipulation**: Impersonate tokens using `steal_token` or `make_token` tasks.
- **Injection**: `execute_pe`, `execute_shellcode`, and `inject` commands for memory-only payload delivery.

### HTTP C2 Profile Configuration
We configure the HTTP profile to mimic standard browser traffic:

```json
{
  "callback_host": "https://updates.microsoft-cdn.net",
  "callback_port": 443,
  "callback_interval": 5,
  "headers": {
    "User-Agent": "Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36",
    "Accept": "text/html,application/xhtml+xml,application/xml;q=0.9",
    "Accept-Language": "en-US,en;q=0.9"
  },
  "get_uri": "/content/updates/check",
  "post_uri": "/content/updates/apply"
}
```

---

## Collaborative Red Teaming

Mythic supports multiple operators simultaneously:
- Each operator connects to the Mythic server using API tokens.
- Tasks assigned to agents are tracked per operator with timestamps.
- The **Graph View** visualizes agent connections and network topology for multi-pivot engagements.
