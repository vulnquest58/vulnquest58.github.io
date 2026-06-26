---
layout: page
title: "Bug Bounty: Enumeration Phase"
subtitle: "Deep dive into web technologies, endpoints, and hidden parameters"
permalink: /bugbounty/methodology/enumeration/
---

## 🎯 Phase Overview
Enumeration is the art of deep inspection. Once live hosts are identified during reconnaissance, we dive deep into the directory structures, configuration routes, APIs, and client-side code of each asset to uncover hidden entry points.

```mermaid
graph TD
    Asset[Live HTTP/S Asset] --> JS[JavaScript Analysis]
    Asset --> Directory[Directory Fuzzing]
    Asset --> API[API Route Parsing]
    
    JS --> JSLink[LinkFinder / subjs]
    Directory --> FFUF[ffuf / gobuster]
    API --> Kiterunner[kiterunner]
    
    JSLink --> Params[Parameter Discovery (Arjun / x8)]
    FFUF --> Params
    Kiterunner --> Params
    
    Params --> AttackSurface[Exploitation Candidates]
```

---

## 📜 1. JavaScript Discovery & Analysis

Modern applications offload routing and application logic to client-side JavaScript. Reading these scripts can reveal hidden endpoints, API keys, and internal structures.

### A. Extracting JS Files
We extract all JavaScript links loaded by a web application:

```bash
# subjs finds Javascript files from list of URLs
cat live_web.txt | subjs | tee js_files.txt

# Download all Javascript files to local folder for static review
mkdir -p downloaded_js && cd downloaded_js
wget -i ../js_files.txt
```

### B. Extracting Links & Endpoints from JS
We scan the downloaded JS files to find API endpoints and query parameters:

```bash
# LinkFinder searches for endpoints using regular expressions
python3 linkfinder.py -i https://target.com/assets/app.js -o cli
```

---

## 📂 2. Directory Fuzzing & Resource Discovery

Directory brute-forcing helps discover hidden panels, backup directories, configuration files, or logs.

### A. High-Speed Web Fuzzing
Using customized wordlists (e.g. Assetnote lists, raft list), we search for paths:

```bash
# FFUF for fast recursive directory fuzzing
ffuf -w /usr/share/seclists/Discovery/Web-Content/raft-large-directories.txt \
     -u https://target.com/FUZZ \
     -mc 200,301,302,403 -recursion -recursion-depth 2 -o ffuf_results.json
```

### B. Backups & Configuration Files Fuzzing
Fuzzing for common extensions like `.bak`, `.zip`, `.git`, `.env` to leak database credentials or source code:

```bash
# FFUF targeting extensions
ffuf -w common_filenames.txt -e .bak,.zip,.conf,.env,.git,.tar.gz \
     -u https://target.com/FUZZ -mc 200 -o sensitive_files.json
```

---

## 🔌 3. API & Parameter Discovery

API endpoints and parameters are often hidden from plain sight.

### A. API Route Enumeration
Using specialized tools targeting common API layouts (REST, GraphQL, Soap):

```bash
# Kiterunner scans for APIs using built-in route datasets
kr scan https://api.target.com -A=apiroutes-210228 -o api_scan.txt
```

### B. Hidden Parameter Guessing
Parameter discovery (e.g., finding a debug parameter like `?debug=true` or `?admin=1`):

```bash
# Arjun detects HTTP parameters using GET, POST, or JSON structures
arjun -u https://target.com/api/user -m GET -oT params.txt

# x8 is an ultra-fast parameter scanner for complex injections
x8 -u "https://target.com/index.php" -w parameters_list.txt
```
