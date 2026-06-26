---
layout: page
title: "Tool Wiki: FFUF"
subtitle: "Fast web fuzzer for directory, virtual host, and parameter discovery"
permalink: /tools/fuzzing/ffuf/
---

## <span class="logo-text">FFUF (Fuzz Faster U Fool)</span>

<div class="tool-badges">
  <span class="badge badge-info">Category: Fuzzing & Inputs</span>
  <span class="badge badge-success">Language: Go</span>
  <span class="badge badge-warning">Type: Active Fuzzer</span>
</div>

### 📘 Definition & Purpose
**FFUF** is an extremely fast web fuzzer written in Go. It is used to brute-force directories, virtual host headers, POST body elements, and query parameters.

### 🧪 Core Mechanics
FFUF takes a wordlist and injects each word into the defined `FUZZ` placeholder in the HTTP request. It utilizes parallel HTTP requests to scan thousands of paths per minute. You can filter responses based on size (`-fs`), words count (`-fw`), lines count (`-fl`), or HTTP status code (`-fc`).

### 🚀 Usage & Cheat Sheet
```bash
# Directory brute-forcing using a standard wordlist
ffuf -w wordlist.txt -u https://target.com/FUZZ

# Filter out common 404 response sizes (e.g. size 4242)
ffuf -w wordlist.txt -u https://target.com/FUZZ -fs 4242

# Fuzzing POST JSON data parameters
ffuf -w user_names.txt -u https://target.com/api/login -X POST \
     -H "Content-Type: application/json" -d '{"username": "FUZZ", "password": "password123"}' \
     -mr "success"

# Recursive fuzzing of paths
ffuf -w wordlist.txt -u https://target.com/FUZZ -recursion -recursion-depth 2 -mc 200,301,302
```

---

### 🔗 Integration
This tool is utilized across the:
- [2024 Enumeration Stage]({{ '/bugbounty/methodology/2024/enumeration/' | relative_url }})
- [2025 Enumeration Stage]({{ '/bugbounty/methodology/2025/enumeration/' | relative_url }})
- [2026 Enumeration Stage]({{ '/bugbounty/methodology/2026/enumeration/' | relative_url }})
