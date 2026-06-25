---
layout: page
title: Lab Manager
subtitle: Virtual machine and container orchestration for security labs
permalink: /tools/lab-manager/
---

## Lab Manager

**Lab Manager** is a local infrastructure orchestration tool that automates the provisioning, configuration, and teardown of vulnerable security lab environments. It supports both VMware/VirtualBox VMs (via Vagrant) and Docker containers, and includes pre-built environment templates for common attack scenarios.

<div class="tool-badges">
  <span class="badge badge-language">Python</span>
  <span class="badge badge-language">Bash</span>
  <span class="badge badge-language">Vagrant</span>
  <span class="badge badge-language">Docker Compose</span>
  <span class="badge badge-status badge-success">Active Development</span>
</div>

---

## Core Features

- **One-command lab deployment**: Spin up a full Active Directory lab or web app environment in minutes.
- **Snapshot management**: Automatically take VM snapshots at defined stages to easily revert to a clean state.
- **Network isolation**: Creates isolated internal virtual networks using NAT or host-only adapters to prevent accidental traffic leakage.
- **Resource profiles**: Tune CPU/RAM allocations per lab type (light, standard, heavy).
- **Lab catalog**: Pre-built templates for 10+ common lab environments.

---

## Available Lab Templates

```bash
# List all available lab templates
lab-manager list

┌──────────────────────────────────────────────────────┐
│  Lab Manager v1.3.0 — Available Environments        │
├──────────────────┬────────────────┬──────────────────┤
│ Template Name    │ Type           │ Resources        │
├──────────────────┼────────────────┼──────────────────┤
│ ad-basic         │ VMware/Vagrant │ 2 VMs, 8GB RAM   │
│ ad-full          │ VMware/Vagrant │ 4 VMs, 16GB RAM  │
│ web-owasp        │ Docker         │ 5 containers     │
│ web-api          │ Docker         │ 3 containers     │
│ cloud-aws-sim    │ Docker         │ 4 containers     │
│ mobile-android   │ Docker+AVD     │ 2 containers     │
│ linux-privesc    │ VMware/Vagrant │ 1 VM, 2GB RAM    │
└──────────────────┴────────────────┴──────────────────┘
```

---

## Usage

### Deploy a Lab

```bash
# Deploy the full Active Directory lab
lab-manager deploy --template ad-full

# Deploy a web application lab
lab-manager deploy --template web-owasp

# Deploy with custom resource profile
lab-manager deploy --template ad-basic --profile light
```

### Snapshot Management

```bash
# Take a named snapshot of all VMs in a running lab
lab-manager snapshot --name "pre-exploit"

# List all snapshots
lab-manager snapshot --list

# Restore to a previous state
lab-manager snapshot --restore "pre-exploit"
```

### Lab Teardown

```bash
# Suspend all VMs (save state for later)
lab-manager suspend

# Destroy all VMs and clean up resources
lab-manager destroy --template ad-full
```

---

## Lab Template Structure

```yaml
# templates/ad-full.yaml
name: ad-full
description: "Full Active Directory forest with 2 DCs, 1 server, and 1 workstation"
type: vagrant
network:
  name: "ad-lab-net"
  adapter: "host-only"
  subnet: "192.168.100.0/24"

machines:
  - name: DC01
    box: "gusztavvargadr/windows-server"
    os: Windows Server 2019
    ip: 192.168.100.10
    memory: 4096
    cpus: 2
    provision:
      - script: "scripts/install-ad-dc.ps1"
      - args: "--domain corp.lab --netbios CORP"

  - name: WS01
    box: "gusztavvargadr/windows-10"
    os: Windows 10
    ip: 192.168.100.20
    memory: 2048
    cpus: 2
    provision:
      - script: "scripts/join-domain.ps1"
      - args: "--domain corp.lab --dc 192.168.100.10"

snapshots:
  - name: "clean-state"
    trigger: "after-provision"
```

---

## GitHub Repository

> 🔗 [github.com/vulnquest58/lab-manager](https://github.com/vulnquest58/lab-manager)
