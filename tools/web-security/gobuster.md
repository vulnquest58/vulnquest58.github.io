---
layout: page
title: "Tool Wiki: Gobuster"
subtitle: "Stable directory, file, and DNS brute-forcer"
permalink: /tools/web-security/gobuster/
---

## <span class="logo-text">Gobuster</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Web Application Security</span>
  <span class="badge badge-success">Language: Go</span>
  <span class="badge badge-warning">Type: Active Brute-Forcer</span>
</div>

### 📘 Definition & Purpose
**Gobuster** is a directory, file, DNS, and VHost brute-forcer written in Go. It is stable and highly suited for recursive directory scans.

### 🧪 Core Mechanics
Gobuster takes a list of filenames or directories and issues HTTP GET requests to check for the existence of resources (looking for 200, 204, 301, 302, 307, or 403 responses).

### 🚀 Usage & Cheat Sheet
```bash
# Brute-force directories with extensions (.php, .html, .txt)
gobuster dir -u https://target.com -w common.txt -x php,html,txt

# VHost domain discovery
gobuster vhost -u https://target.com -w vhost_wordlist.txt

# DNS subdomain brute-forcing
gobuster dns -d target.com -w subdomains_wordlist.txt
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Enumeration Stage]({{ '/bugbounty/methodology/2024/enumeration/' | relative_url }})
- [2025 Enumeration Stage]({{ '/bugbounty/methodology/2025/enumeration/' | relative_url }})
- [2026 Enumeration Stage]({{ '/bugbounty/methodology/2026/enumeration/' | relative_url }})
