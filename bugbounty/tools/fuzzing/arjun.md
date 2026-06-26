---
layout: page
title: "Tool Wiki: Arjun"
subtitle: "HTTP parameter discovery suite"
permalink: /bugbounty/tools/fuzzing/arjun/
---

## <span class="logo-text">Arjun</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Fuzzing & Inputs</span>
  <span class="badge badge-success">Language: Python</span>
  <span class="badge badge-warning">Type: Parameter Guessing</span>
</div>

### 📘 Definition & Purpose
**Arjun** is an HTTP parameter discovery suite built in Python. It detects query parameters (GET, POST, XML, JSON) for web endpoints.

### 🧪 Core Mechanics
Arjun uses a smart heuristic approach to detect parameters. Instead of checking one by one, it queries parameters in batches. If the HTTP response size, headers, or structure changes slightly, it performs binary splits to pinpoint the exact parameter that caused the difference.

### 🚀 Usage & Cheat Sheet
```bash
# Scan a GET endpoint for hidden parameters
arjun -u https://target.com/api/details -m GET

# Scan a JSON POST endpoint
arjun -u https://target.com/api/register -m POST --json

# Set custom headers (e.g. cookie authentication)
arjun -u https://target.com/api/user -H "Cookie: session=123"
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Enumeration Stage]({{ '/bugbounty/methodology/2024/enumeration/' | relative_url }})
- [2025 Enumeration Stage]({{ '/bugbounty/methodology/2025/enumeration/' | relative_url }})
- [2026 Enumeration Stage]({{ '/bugbounty/methodology/2026/enumeration/' | relative_url }})
