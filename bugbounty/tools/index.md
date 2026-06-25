---
layout: page
title: Bug Bounty Tools
subtitle: Essential tools and scripts for vulnerability hunting
---

## My Toolkit

A curated collection of tools I use daily for bug bounty hunting.

## Reconnaissance Tools

### Subdomain Enumeration

```bash
# Subfinder - Fast passive subdomain discovery
subfinder -d target.com -o subdomains.txt

# Amass - Comprehensive subdomain enumeration
amass enum -passive -d target.com -o amass.txt

# Assetfinder - Quick subdomain finder
assetfinder --subs-only target.com | tee assetfinder.txt
```

### Port Scanning

```bash
# Nmap - Comprehensive port scanning
nmap -sC -sV -oN scan.txt -iL hosts.txt

# Naabu - Fast port scanner
naabu -list hosts.txt -o ports.txt

# Masscan - Ultra-fast port scanning
masscan -iL hosts.txt -p1-65535 --rate=10000
```

### Technology Detection

```bash
# httpx - HTTP probing
httpx -l subdomains.txt -tech-detect -status-code

# WhatWeb - Web technology identifier
whatweb -i urls.txt

# Wappalyzer - Browser extension
# Install from browser store
```

## Vulnerability Scanning

### Automated Scanners

```bash
# Nuclei - Template-based vulnerability scanner
nuclei -l urls.txt -t nuclei-templates/ -o nuclei.txt

# Nmap NSE scripts
nmap --script vuln -iL hosts.txt

# Nikto - Web server scanner
nikto -h https://target.com
```

### Web Application Testing

```bash
# SQLMap - SQL injection testing
sqlmap -u "https://target.com/page?id=1" --batch

# XSStrike - XSS detection
python xsstrike.py -u "https://target.com/page?q=test"

# Commix - Command injection
python commix.py --url="https://target.com/page?cmd=test"
```

## Custom Tools

### Parameter Discovery

```bash
# Arjun - HTTP parameter discovery
arjun -u https://target.com/page -oT params.txt

# x8 - Hidden parameter finder
x8 -u https://target.com/page -m GET,POST
```

### JavaScript Analysis

```bash
# subjs - JavaScript file discovery
subjs target.com | grep -E "\.js$"

# getJS - Download JavaScript files
getJS --url https://target.com --output js.txt

# LinkFinder - Endpoint discovery in JS
python linkfinder.py -i js_file.js -o cli
```

## Burp Suite Extensions

### Essential Extensions

1. **Autorize** - Authorization testing
2. **Logger++** - Enhanced logging
3. **JSON Web Tokens** - JWT manipulation
4. **Hackvertor** - Encoding/decoding
5. **Param Miner** - Parameter discovery
6. **Active Scan++** - Enhanced scanning
7. **Turbo Intruder** - Fast brute-forcing

## Browser Extensions

### Security Testing

- **Wappalyzer** - Technology detection
- **FoxyProxy** - Proxy management
- **Cookie Editor** - Cookie manipulation
- **HackBar** - Testing toolkit
- **JSON Viewer** - JSON formatting

## Wordlists

### Custom Wordlists

```bash
# Directory brute-forcing
/usr/share/wordlists/dirb/common.txt
/usr/share/seclists/Discovery/Web-Content/

# Subdomain wordlists
/usr/share/seclists/Discovery/DNS/subdomains-top1million-5000.txt

# Password wordlists
/usr/share/wordlists/rockyou.txt
```

## Automation Scripts

### Recon Pipeline

```bash
#!/bin/bash
# Automated reconnaissance script

DOMAIN=$1
OUTPUT_DIR="recon_$DOMAIN"

mkdir -p $OUTPUT_DIR

# Subdomain enumeration
echo "[*] Enumerating subdomains..."
subfinder -d $DOMAIN -o $OUTPUT_DIR/subdomains.txt
amass enum -passive -d $DOMAIN -o $OUTPUT_DIR/amass.txt

# Combine and sort
cat $OUTPUT_DIR/*.txt | sort -u > $OUTPUT_DIR/all_subdomains.txt

# HTTP probing
echo "[*] Probing HTTP services..."
httpx -l $OUTPUT_DIR/all_subdomains.txt -o $OUTPUT_DIR/live_hosts.txt

# Port scanning
echo "[*] Scanning ports..."
naabu -l $OUTPUT_DIR/live_hosts.txt -o $OUTPUT_DIR/ports.txt

echo "[+] Reconnaissance complete!"
```

### Vulnerability Scanning

```bash
#!/bin/bash
# Automated vulnerability scanning

TARGETS=$1
OUTPUT_DIR="scan_results"

mkdir -p $OUTPUT_DIR

# Nuclei scan
echo "[*] Running Nuclei scan..."
nuclei -l $TARGETS -t nuclei-templates/ -severity critical,high -o $OUTPUT_DIR/nuclei.txt

# Generate report
echo "[+] Scan complete! Results in $OUTPUT_DIR"
```

## Installation

### Quick Setup

```bash
# Install Go tools
go install -v github.com/projectdiscovery/subfinder/v2/cmd/subfinder@latest
go install -v github.com/projectdiscovery/httpx/cmd/httpx@latest
go install -v github.com/projectdiscovery/nuclei/v2/cmd/nuclei@latest

# Install Python tools
pip install sqlmap xsstrike arjun

# Clone repositories
git clone https://github.com/OWASP/Amass.git
git clone https://github.com/sqlmapproject/sqlmap.git
```

## Best Practices

✅ **Do**:
- Keep tools updated
- Use virtual environments
- Document your workflow
- Test tools in lab first
- Respect rate limits

❌ **Don't**:
- Run destructive scans without permission
- Overload target servers
- Ignore tool errors
- Use outdated tools
- Share API keys publicly

## Resources

- [Awesome Bug Bounty Tools](https://github.com/vavkamil/awesome-bugbounty-tools)
- [Bug Bounty Methodology](../methodology.md)
- [Custom Scripts](../../tools/custom-scripts/index.md)