---
layout: page
title: "2024 Methodology: Reconnaissance"
subtitle: "Classic subdomain mapping and passive discovery workflows"
permalink: /bugbounty/methodology/2024/reconnaissance/
---

## 🔍 Subdomain Harvesting & Passive Sweep (2024)

In 2024, reconnaissance is focused on passive asset gathering. The objective is to sweep public intelligence data without sending direct request packets to the target’s web servers.

### 🌐 Subdomain Gathering
We query public search databases using [Subfinder]({{ '/bugbounty/tools/recon/subfinder/' | relative_url }}) and [OWASP Amass]({{ '/bugbounty/tools/recon/amass/' | relative_url }}):

```bash
# Subfinder harvests subdomains passively
subfinder -d target.com -o passive_subdomains.txt

# Amass passive scanning
amass enum -passive -d target.com -o amass_passive.txt
```

### 📜 Certificate Transparency Logs
Every SSL/TLS certificate issued is logged. Checking these logs can reveal newly registered subdomains:

```bash
# Query crt.sh database for wildcards
curl -s "https://crt.sh/?q=%25.target.com&output=json" | jq -r '.[].name_value' | sed 's/\*\.//g' | sort -u > cert_subdomains.txt
```

### 🎯 Live Service Mapping
Once the list is gathered, we sweep for open TCP ports using [Naabu]({{ '/bugbounty/tools/recon/naabu/' | relative_url }}):

```bash
# Naabu fast port scanning
naabu -list passive_subdomains.txt -p 80,443,8080,8443 -o open_ports.txt
```

---

### 🔗 Navigation
- [Go to 2024 Enumeration Stage]({{ '/bugbounty/methodology/2024/enumeration/' | relative_url }})
- [Return to 2024 Dashboard]({{ '/bugbounty/methodology/2024/' | relative_url }})
