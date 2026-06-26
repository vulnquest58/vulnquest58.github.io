---
layout: page
title: "Tool Wiki: Naabu"
subtitle: "High-speed TCP/UDP port scanner"
permalink: /tools/information-gathering/naabu/
---

## <span class="logo-text">Naabu</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Information Gathering</span>
  <span class="badge badge-success">Language: Go</span>
  <span class="badge badge-warning">Type: Active (Port Scanner)</span>
</div>

### 📘 Definition & Purpose
**Naabu** is a high-speed TCP/UDP port scanner written in Go. It is designed to quickly scan thousands of hosts to locate open service ports.

### 🧪 Core Mechanics
Naabu utilizes raw socket parsing to perform SYN scans. It sends SYN packets to a list of target IPs/ports and listens for SYN-ACK or RST responses to identify open ports at lightning speed.

### 🚀 Usage & Cheat Sheet
```bash
# Scan a list of domains for standard web ports
naabu -list subdomains.txt -p 80,443,8080,8443 -o open_ports.txt

# Full port scan (all 65,535 ports) on a target host
naabu -host target.com -p - -rate 1000 -o target_full_ports.txt

# Pipe subdomains from other tools directly into Naabu
subfinder -d target.com -silent | naabu -p 80,443 -silent
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Reconnaissance Stage]({{ '/bugbounty/methodology/2024/reconnaissance/' | relative_url }})
- [2025 Reconnaissance Stage]({{ '/bugbounty/methodology/2025/reconnaissance/' | relative_url }})
- [2026 Reconnaissance Stage]({{ '/bugbounty/methodology/2026/reconnaissance/' | relative_url }})
