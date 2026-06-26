---
layout: page
title: "Custom Repository: My Repo"
subtitle: "In-house offensive tooling and automation scripts"
permalink: /bugbounty/tools/my-repo/
---

## 🛠️ Custom Tooling & Development

This section covers custom-built utilities designed to automate and support active engagements, vulnerability tracing, local environment orchestration, and automated setup.

---

## 🔎 1. VULNTRACE

### 📘 Definition
**Vulntrace** is an advanced dynamic vulnerability analysis and runtime tracing tool. It monitors system calls, memory allocations, and program flows of binary processes to automatically flag potential memory leaks, buffer overflows, and logical validation bypasses.

### 🧪 Design & Execution Engine
Unlike static scanners, Vulntrace acts as an active debugger (abusing `ptrace` on Linux or debugging APIs on Windows) to dynamically inspect instruction executions in real-time. It compares arguments of dangerous functions (e.g. `strcpy`, `memcpy`, `system`) with patterns of user-controlled inputs to detect flows leading to remote code execution.

### 🚀 Usage & Common Commands
```bash
# Start tracing a binary in real-time
vulntrace --target /usr/bin/vuln_app --args "-p 8080"

# Monitor system calls and detect memory leak allocations
vulntrace --pid 10245 --detect-leaks --output trace_log.json

# Analyze heap transitions for buffer anomalies
vulntrace --target ./app --heap-audit
```

---

## 💻 2. Kali Master

### 📘 Definition
**Kali Master** is a comprehensive automated provisioning and bash-scripted configuration framework. It converts a fresh Kali Linux installation into a fully customized, production-ready offensive security environment within minutes.

### 🧪 Automation Setup
It automates the installation of standard tools (e.g. Go-based tools, Python scripts), imports customized API key profiles for recon engines, tweaks kernel network parameters for high-speed packet scanning, and sets up visual desktop adjustments.

### 🚀 Usage & Common Commands
```bash
# Run the complete configuration pipeline
sudo ./kali-master.sh --full

# Install and configure only web exploitation packages
sudo ./kali-master.sh --install-category web

# Import API keys and configure search profiles
sudo ./kali-master.sh --import-keys config_keys.json
```

---

## 📦 3. Lab Manager

### 📘 Definition
**Lab Manager** is a container and virtual machine orchestration dashboard. It compiles, deploys, and terminates vulnerable laboratories locally to allow developers and hunters to practice safe exploitation.

### 🧪 Orchestration Architecture
Abusing Docker and Vagrant configurations, it dynamically sets up multi-host active directory forests, insecure REST APIs, and vulnerable database clusters in complete network isolation.

### 🚀 Usage & Common Commands
```bash
# Deploy a vulnerable Active Directory lab locally
lab-manager --deploy ad-forest-v1

# Spin up a vulnerable web application lab (SSRF / SQLi)
lab-manager --deploy web-labs-docker --port 9090

# Stop all lab services and purge containers
lab-manager --terminate --all
```
