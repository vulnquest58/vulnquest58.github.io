---
layout: page
title: "Tool Wiki: Lab Manager"
subtitle: "Vulnerable environment orchestration and local deployment dashboard"
permalink: /bugbounty/tools/my-repo/lab-manager/
---

## <span class="logo-text">Lab Manager</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Custom Tool (My Repo)</span>
  <span class="badge badge-success">Language: Python / Shell</span>
  <span class="badge badge-warning">Type: Container Orchestrator</span>
</div>

### 📘 Definition & Purpose
**Lab Manager** is a container and virtual machine orchestration dashboard. It compiles, deploys, and terminates vulnerable laboratories locally to allow developers and hunters to practice safe exploitation.

### 🧪 Core Mechanics
Abusing Docker and Vagrant configurations, it dynamically sets up multi-host active directory forests, insecure REST APIs, and vulnerable database clusters in complete network isolation.

### 🚀 Usage & Cheat Sheet
```bash
# Deploy a vulnerable Active Directory lab locally
lab-manager --deploy ad-forest-v1

# Spin up a vulnerable web application lab (SSRF / SQLi)
lab-manager --deploy web-labs-docker --port 9090

# Stop all lab services and purge containers
lab-manager --terminate --all
```

---

### 🔗 Developer Repository
- [View GitHub Profile / myrepo]({{' https://github.com/vulnquest58 '}})
