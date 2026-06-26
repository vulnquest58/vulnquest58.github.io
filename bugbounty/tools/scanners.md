---
layout: page
title: "Specialty Guide: Vulnerability Scanners"
subtitle: "Automated vulnerability scanning and security testing tools"
permalink: /bugbounty/tools/scanners/
---

## 🔬 Automated Vulnerability Scanners

Vulnerability scanners automate the detection of known CVEs, misconfigurations, default credentials, and common vulnerabilities.

---

## 🎯 1. Nuclei

### 📘 Definition
**Nuclei** is a highly customizable, template-based vulnerability scanner written in Go. It allows developers and hunters to write YAML templates that define HTTP/TCP/DNS/File requests and verify responses using string, hex, or regex matchers.

### 🧪 Template-Based Scanning
Nuclei sends rapid network requests based on templates stored in the community Nuclei templates repository. It matches responses against predefined signatures to check for vulnerabilities like exposed `.git` folders, SSRF, XSS, default panels, and critical CVEs.

### 🚀 Usage & Common Commands
```bash
# Scan a list of hosts using all critical and high severity templates
nuclei -l live_web.txt -severity critical,high

# Target a specific vulnerability or CVE template
nuclei -u https://target.com -t cves/2021/CVE-2021-44228.yaml

# Scan for exposed panel files and configuration leaks
nuclei -u https://target.com -t exposures/
```

---

## 💽 2. Nikto

### 📘 Definition
**Nikto** is a classic open-source web server scanner written in Perl. It scans web servers for over 6,700 potentially dangerous files/programs, outdated server versions, and configuration issues.

### 🧪 Server Profiling
Nikto queries typical index paths, analyzes HTTP header responses for security headers (e.g. missing `X-Frame-Options`), audits CGI directories, and brute-forces default credential logins.

### 🚀 Usage & Common Commands
```bash
# Basic web server scan
nikto -h https://target.com

# Scan a target host and save results in HTML format
nikto -h https://target.com -ssl -o nikto_scan.html -Format htm
```

---

## 🛡️ 3. Nmap NSE (Nmap Scripting Engine)

### 📘 Definition
The **Nmap Scripting Engine (NSE)** allows users to write scripts in Lua to automate network checks, vulnerability detection, and system profiling.

### 🧪 Active Probe Testing
Nmap executes Lua scripts during the port scan phase, interacting directly with TCP/UDP sockets to verify vulnerabilities.

### 🚀 Usage & Common Commands
```bash
# Check for common vulnerabilities using the 'vuln' script category
nmap --script vuln -p 80,443,8080 target.com

# Audit an SMB server for vulnerabilities (e.g. MS17-010 EternalBlue)
nmap --script smb-vuln-ms17-010 -p 445 10.10.10.40
```
