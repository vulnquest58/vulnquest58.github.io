---
layout: page
title: Covenant C2 Configuration
subtitle: Collaborative .NET Command and Control platform
permalink: /redteam/c2-frameworks/covenant/
---

## Covenant .NET C2

Covenant is a collaborative C2 platform designed for .NET developers. Its agent, the Grunt, is written in C#, allowing compilation of tasks directly on the server before execution in memory on the victim host.

### Architecture & Installation

Covenant is installed using docker-compose to establish the web database portal:

```bash
git clone --recursive https://github.com/cobbr/Covenant
cd Covenant/Covenant
docker-compose up --build
```

Access the web interface at `https://localhost:7443` to configure user profiles and setup listeners.

---

## Grunt Implant & Evasion

Covenant implants (Grunts) support compilation options like .NET versioning (e.g., v3.5 or v4.0), certificate pinning, and connection jitter.

### Assembly Injection & Execution
A major feature of Covenant is the ability to run .NET assemblies directly in memory using the `Assembly` execution module. This allows us to load tools like SharpHound or Rubeus without having to write them to disk.

```text
# Grunt console task execution
Grunt > execute-assembly /opt/tools/SharpHound.exe -c All
```

---

## Malleable C2 & Profile Management

We configure **Malleable C2 Profiles** inside Covenant to encrypt our HTTP traffic. By defining specific request headers and response structures, we mimic standard API traffic (such as Microsoft Office 365 login requests) to evade network-level threat detection systems.
