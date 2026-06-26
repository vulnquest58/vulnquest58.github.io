---
layout: page
title: "Tool Wiki: Nmap Scripting Engine (NSE)"
subtitle: "Network exploration and vulnerability scripting framework"
permalink: /bugbounty/tools/scanners/nmap/
---

## <span class="logo-text">Nmap Scripting Engine (NSE)</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Vulnerability Scanners</span>
  <span class="badge badge-success">Language: C++ / Lua</span>
  <span class="badge badge-warning">Type: Port Scanner & Script Engine</span>
</div>

### 📘 Definition & Purpose
The **Nmap Scripting Engine (NSE)** allows users to write scripts in Lua to automate network checks, vulnerability detection, and system profiling.

### 🧪 Core Mechanics
Nmap executes Lua scripts during the port scan phase, interacting directly with TCP/UDP sockets to verify vulnerabilities.

### 🚀 Usage & Cheat Sheet
```bash
# Check for common vulnerabilities using the 'vuln' script category
nmap --script vuln -p 80,443,8080 target.com

# Audit an SMB server for vulnerabilities (e.g. MS17-010 EternalBlue)
nmap --script smb-vuln-ms17-010 -p 445 10.10.10.40

# Run safe detection scripts and perform OS detection
nmap -sV -sC -O target.com -oN nmap_safe_scan.txt
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2024/vulnerability-analysis/' | relative_url }})
- [2025 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2025/vulnerability-analysis/' | relative_url }})
- [2026 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2026/vulnerability-analysis/' | relative_url }})
