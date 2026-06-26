---
layout: page
title: "Tool Wiki: Subfinder"
subtitle: "Fast passive subdomain discovery engine"
permalink: /bugbounty/tools/recon/subfinder/
---

## <span class="logo-text">Subfinder</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Reconnaissance</span>
  <span class="badge badge-success">Language: Go</span>
  <span class="badge badge-warning">Type: Passive</span>
</div>

### 📘 Definition & Purpose
**Subfinder** is a fast, passive subdomain discovery tool built in Go. It queries various public, historical, and threat intelligence sources to harvest subdomain lists.

### 🧪 Core Mechanics
Subfinder operates without sending any direct traffic to the target's servers. Instead, it interacts with APIs (such as VirusTotal, Shodan, Censys, SecurityTrails, and DNSDumpster) to collect records.

### 🚀 Usage & Cheat Sheet
```bash
# Basic passive subdomain scan for a domain
subfinder -d target.com -o subdomains.txt

# Run scan using all available passive search engines and threads
subfinder -d target.com -all -t 50 -silent -o subdomains_all.txt

# Use API keys configuration file for optimized results
subfinder -d target.com -config ~/.config/subfinder/provider-config.yaml -o subdomains_api.txt
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Reconnaissance Stage]({{ '/bugbounty/methodology/2024/reconnaissance/' | relative_url }})
- [2025 Reconnaissance Stage]({{ '/bugbounty/methodology/2025/reconnaissance/' | relative_url }})
- [2026 Reconnaissance Stage]({{ '/bugbounty/methodology/2026/reconnaissance/' | relative_url }})
