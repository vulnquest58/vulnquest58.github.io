---
layout: page
title: "Tool Wiki: OWASP Amass"
subtitle: "In-depth asset mapping and domain tracking engine"
permalink: /tools/information-gathering/amass/
---

## <span class="logo-text">OWASP Amass</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Information Gathering</span>
  <span class="badge badge-success">Language: Go</span>
  <span class="badge badge-warning">Type: Active & Passive</span>
</div>

### 📘 Definition & Purpose
**OWASP Amass** is an in-depth asset mapping and domain tracking engine. It excels at active and passive subdomain collection, ASN correlation, and DNS resolution.

### 🧪 Core Mechanics
Amass uses advanced DNS harvesting, scraping, and APIs. It combines techniques like:
- **Active Subdomain Bruteforcing**: Querying combinations of words from wordlists.
- **DNS Alteration & Permutation**: Generating subdomains based on existing names (e.g. `dev.target.com` -> `dev-test.target.com`).
- **Reverse DNS Sweeping**: Scanning IP ranges and resolving them back to hostnames.

### 🚀 Usage & Cheat Sheet
```bash
# Passive subdomain enumeration
amass enum -passive -d target.com -o passive_subs.txt

# Active subdomain discovery including bruteforcing and IP sweeps
amass enum -active -d target.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -o active_subs.txt

# ASN discovery to identify target's IP spaces
amass intel -org "Target Corp"

# IP range mapping to locate targets associated with ASN
amass intel -asn 12345 -o asn_ips.txt
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Reconnaissance Stage]({{ '/bugbounty/methodology/2024/reconnaissance/' | relative_url }})
- [2025 Reconnaissance Stage]({{ '/bugbounty/methodology/2025/reconnaissance/' | relative_url }})
- [2026 Reconnaissance Stage]({{ '/bugbounty/methodology/2026/reconnaissance/' | relative_url }})
