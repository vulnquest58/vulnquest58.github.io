---
layout: page
title: "Tool Wiki: Nuclei"
subtitle: "Fast and customizable template-based vulnerability scanner"
permalink: /tools/web-security/nuclei/
---

## <span class="logo-text">Nuclei</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Web Application Security</span>
  <span class="badge badge-success">Language: Go</span>
  <span class="badge badge-warning">Type: Template-Based Scan</span>
</div>

### 📘 Definition & Purpose
**Nuclei** is a highly customizable, template-based vulnerability scanner written in Go. It allows developers and hunters to write YAML templates that define HTTP/TCP/DNS/File requests and verify responses using string, hex, or regex matchers.

### 🧪 Core Mechanics
Nuclei sends rapid network requests based on templates stored in the community Nuclei templates repository. It matches responses against predefined signatures to check for vulnerabilities like exposed `.git` folders, SSRF, XSS, default panels, and critical CVEs.

### 🚀 Usage & Cheat Sheet
```bash
# Scan a list of hosts using all critical and high severity templates
nuclei -l live_web.txt -severity critical,high

# Target a specific vulnerability or CVE template
nuclei -u https://target.com -t cves/2021/CVE-2021-44228.yaml

# Scan for exposed panel files and configuration leaks
nuclei -u https://target.com -t exposures/

# Automatically update templates database
nuclei -update-templates
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2024/vulnerability-analysis/' | relative_url }})
- [2025 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2025/vulnerability-analysis/' | relative_url }})
- [2026 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2026/vulnerability-analysis/' | relative_url }})
