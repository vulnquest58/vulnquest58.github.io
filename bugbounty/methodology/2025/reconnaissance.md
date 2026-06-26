---
layout: page
title: "2025 Methodology: Reconnaissance"
subtitle: "Automated pipelines and live web asset discovery"
permalink: /bugbounty/methodology/2025/reconnaissance/
---

## 🔍 Automated Recon Pipelines & Probing (2025)

The 2025 reconnaissance model coordinates automated pipelines to instantly map out the target attack surface and identify active web servers.

### 🛠️ Continuous Recon Scripting
We automate subdomain harvesting using [Subfinder]({{ '/tools/subdomain-dns/subfinder/' | relative_url }}) and [OWASP Amass]({{ '/tools/subdomain-dns/amass/' | relative_url }}):

```bash
# Combine passive data sources
subfinder -d target.com -silent -o subfinder.txt
amass enum -passive -d target.com -silent -o amass.txt
cat subfinder.txt amass.txt | sort -u > all_subdomains.txt
```

### ⚡ Live Service Identification
We run active port discovery using [Naabu]({{ '/tools/recon-osint/naabu/' | relative_url }}) and identify live web headers using `httpx`:

```bash
# Rapid port check
naabu -list all_subdomains.txt -p 80,443,8080,8443 -silent -o live_ports.txt

# Technology and title resolution using httpx
httpx -l live_ports.txt -sc -title -tech-detect -o live_web_assets.txt
```

---

### 🔗 Navigation
- [Go to 2025 Enumeration Stage]({{ '/bugbounty/methodology/2025/enumeration/' | relative_url }})
- [Return to 2025 Dashboard]({{ '/bugbounty/methodology/2025/' | relative_url }})


