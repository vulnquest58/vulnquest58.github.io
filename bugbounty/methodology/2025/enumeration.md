---
layout: page
title: "2025 Methodology: Enumeration"
subtitle: "JavaScript mining, API routing, and parameter fuzzing"
permalink: /bugbounty/methodology/2025/enumeration/
---

## 📂 JavaScript Analysis & API Enumeration (2025)

The 2025 enumeration phase focuses on client-side routing structures and unexposed REST/GraphQL API path mappings.

### 📜 JavaScript Mining & URL Discovery
Modern web apps use thick JS bundles. We extract endpoints using `subjs` and `LinkFinder`:

```bash
# Extract JS locations
cat live_web_assets.txt | subjs > js_files.txt

# Extract URLs from JavaScript files
python3 linkfinder.py -i https://target.com/assets/main.js -o cli > extracted_links.txt
```

### 🔌 API Endpoint Resolution
We brute-force API gateways using specialized tools and route files:

```bash
# Kiterunner API route discovery
kr scan https://api.target.com -A=apiroutes-210228 -o api_endpoints.txt
```

### 🔑 Batch Parameter Fuzzing
We guess hidden parameters using [Arjun]({{ '/tools/web-security/arjun/' | relative_url }}) and [x8]({{ '/tools/web-security/x8/' | relative_url }}):

```bash
# Fuzz JSON POST parameter fields
arjun -u https://target.com/api/v2/update -m POST --json

# Run x8 for fast parameter discovery
x8 -u "https://target.com/index.php" -w parameters.txt
```

---

### 🔗 Navigation
- [Go to 2025 Vulnerability Analysis Stage]({{ '/bugbounty/methodology/2025/vulnerability-analysis/' | relative_url }})
- [Return to 2025 Dashboard]({{ '/bugbounty/methodology/2025/' | relative_url }})


