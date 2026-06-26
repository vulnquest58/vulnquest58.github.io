---
layout: page
title: "Tool Wiki: Nikto"
subtitle: "Classic open-source web server scanner"
permalink: /tools/web-security/nikto/
---

## <span class="logo-text">Nikto</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Web Application Security</span>
  <span class="badge badge-success">Language: Perl</span>
  <span class="badge badge-warning">Type: Server Profiler</span>
</div>

### 📘 Definition & Purpose
**Nikto** is a classic open-source web server scanner written in Perl. It scans web servers for over 6,700 potentially dangerous files/programs, outdated server versions, and configuration issues.

### 🧪 Core Mechanics
Nikto queries typical index paths, analyzes HTTP header responses for security headers (e.g. missing `X-Frame-Options`), audits CGI directories, and brute-forces default credential logins.

### 🚀 Usage & Cheat Sheet
```bash
# Basic web server scan
nikto -h https://target.com

# Scan a target host and save results in HTML format
nikto -h https://target.com -ssl -o nikto_scan.html -Format htm

# Scan multiple hosts using a file list
nikto -h hosts.txt -port 80,443 -Format csv -o results.csv
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2024/vulnerability-analysis/' | relative_url }})
- [2025 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2025/vulnerability-analysis/' | relative_url }})
- [2026 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2026/vulnerability-analysis/' | relative_url }})
