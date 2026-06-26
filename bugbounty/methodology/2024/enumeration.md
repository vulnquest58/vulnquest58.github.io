---
layout: page
title: "2024 Methodology: Enumeration"
subtitle: "Classic path brute-forcing and client-side inspection"
permalink: /bugbounty/methodology/2024/enumeration/
---

## 📂 Directory Fuzzing & Client-Side Review (2024)

The 2024 enumeration phase focus is discovering hidden directories, parameters, and sensitive configuration endpoints.

### 📁 Directory Brute-Forcing
We scan targets for administrative path exposures, directories, and configuration backups using [Gobuster]({{ '/bugbounty/tools/fuzzing/gobuster/' | relative_url }}):

```bash
# Gobuster directory fuzzing with standard wordlists
gobuster dir -u https://target.com -w common.txt -x php,html,txt,json
```

### 🔑 Parameter Discovery
Finding hidden variables on the endpoint using [Arjun]({{ '/bugbounty/tools/fuzzing/arjun/' | relative_url }}):

```bash
# Arjun scans GET endpoints for hidden parameters
arjun -u https://target.com/api/details -m GET
```

### 📜 JavaScript Inspection
We search the page source manually or extract endpoints to audit static logic:
1. Load target web page in Burp Suite proxy.
2. Filter for `.js` files in Target history.
3. Review scripts for hardcoded secrets, backup paths, and unauthenticated routes.

---

### 🔗 Navigation
- [Go to 2024 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2024/vulnerability-analysis/' | relative_url }})
- [Return to 2024 Dashboard]({{ '/bugbounty/methodology/2024/' | relative_url }})
