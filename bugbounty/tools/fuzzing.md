---
layout: page
title: "Specialty Guide: Fuzzing & Parameter Discovery"
subtitle: "Tools for directory brute-forcing, API fuzzing, and input discovery"
permalink: /bugbounty/tools/fuzzing/
---

## 📂 Web Fuzzing & Input Discovery Tools

Fuzzing is the process of brute-forcing directories, URLs, parameters, and payloads to locate hidden files, administrative interfaces, and application variables.

---

## ⚡ 1. FFUF (Fuzz Faster U Fool)

### 📘 Definition
**FFUF** is an extremely fast web fuzzer written in Go. It is used to brute-force directories, virtual host headers, POST body elements, and query parameters.

### 🧪 Brute-Forcing & Filtration
FFUF works by taking a wordlist and injecting each word into the defined `FUZZ` placeholder in the HTTP request. It utilizes parallel HTTP requests to scan thousands of paths per minute. You can filter responses based on size (`-fs`), words count (`-fw`), lines count (`-fl`), or HTTP status code (`-fc`).

### 🚀 Usage & Common Commands
```bash
# Directory brute-forcing using a standard wordlist
ffuf -w wordlist.txt -u https://target.com/FUZZ

# Filter out common 404 response sizes (e.g. size 4242)
ffuf -w wordlist.txt -u https://target.com/FUZZ -fs 4242

# Fuzzing POST JSON data parameters
ffuf -w user_names.txt -u https://target.com/api/login -X POST \
     -H "Content-Type: application/json" -d '{"username": "FUZZ", "password": "password123"}' \
     -mr "success"
```

---

## 📂 2. Gobuster

### 📘 Definition
**Gobuster** is a directory, file, DNS, and VHost brute-forcer written in Go. It is stable and highly suited for recursive directory scans.

### 🧪 Directory Brute-Forcing
Gobuster takes a list of filenames or directories and issues HTTP GET requests to check for the existence of resources (looking for 200, 204, 301, 302, 307, or 403 responses).

### 🚀 Usage & Common Commands
```bash
# Brute-force directories with extensions (.php, .html, .txt)
gobuster dir -u https://target.com -w common.txt -x php,html,txt

# VHost domain discovery
gobuster vhost -u https://target.com -w vhost_wordlist.txt
```

---

## 🔑 3. Arjun

### 📘 Definition
**Arjun** is an HTTP parameter discovery suite built in Python. It detects query parameters (GET, POST, XML, JSON) for web endpoints.

### 🧪 Parameter Guessing
Arjun uses a smart heuristic approach to detect parameters. Instead of checking one by one, it queries parameters in batches. If the HTTP response size, headers, or structure changes slightly, it performs binary splits to pinpoint the exact parameter that caused the difference.

### 🚀 Usage & Common Commands
```bash
# Scan a GET endpoint for hidden parameters
arjun -u https://target.com/api/details -m GET

# Scan a JSON POST endpoint
arjun -u https://target.com/api/register -m POST --json
```

---

## 🚀 4. x8

### 📘 Definition
**x8** is an ultra-fast parameter discovery utility written in Rust, designed to find hidden query parameters and headers.

### 🧪 Dual-Heuristic Discovery
x8 is extremely fast and optimized for large wordlists. It parses headers, bodies, cookies, and HTTP variables using custom algorithms to identify differences in WAF behaviors and web server error codes.

### 🚀 Usage & Common Commands
```bash
# Discover hidden parameters in GET requests
x8 -u "https://target.com/" -w parameters.txt

# Discover custom HTTP request headers (e.g. X-Forwarded-For)
x8 -u "https://target.com/" -w headers.txt --proto headers
```
