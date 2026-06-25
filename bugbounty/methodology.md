---
layout: page
title: Bug Bounty Methodology
subtitle: Systematic approach to vulnerability discovery
---

## Introduction

A structured methodology is crucial for successful bug bounty hunting. This guide outlines my proven approach to finding vulnerabilities efficiently and effectively.

## Phase 1: Reconnaissance

### Passive Reconnaissance

**Goal**: Gather information without direct interaction

```bash
# Subdomain enumeration
subfinder -d target.com -o subdomains.txt
amass enum -passive -d target.com

# Technology detection
whatweb -i urls.txt
httpx -l subdomains.txt -tech-detect

# Historical data
waybackurls target.com | sort -u
gau target.com | sort -u
```

### Active Reconnaissance

**Goal**: Discover live assets and endpoints

```bash
# Port scanning
nmap -sC -sV -oN nmap_scan.txt -iL subdomains.txt

# Directory brute-forcing
ffuf -u https://target.com/FUZZ -w wordlist.txt
gobuster dir -u https://target.com -w wordlist.txt

# Parameter discovery
arjun -u https://target.com/page
x8 -u https://target.com/page
```

## Phase 2: Enumeration

### Endpoint Mapping

```bash
# JavaScript analysis
subjs target.com | grep -E "\.js$"
getJS --url https://target.com --output js_files.txt

# API discovery
kiterunner scan https://target.com -A=apiroutes-210228
```

### Technology Stack

Identify:
- Web frameworks (React, Angular, Django, etc.)
- Backend technologies (Node.js, PHP, Python, etc.)
- Databases (MySQL, PostgreSQL, MongoDB, etc.)
- CDNs and WAFs (Cloudflare, Akamai, etc.)

## Phase 3: Vulnerability Testing

### OWASP Top 10 Checklist

- [ ] **A01: Broken Access Control**
  - IDOR testing
  - Privilege escalation
  - Path traversal
  
- [ ] **A02: Cryptographic Failures**
  - Weak encryption
  - Exposed secrets
  - Insecure protocols
  
- [ ] **A03: Injection**
  - SQL injection
  - Command injection
  - XSS (all types)
  
- [ ] **A04: Insecure Design**
  - Business logic flaws
  - Race conditions
  - Missing controls

## Phase 4: Exploitation

### Proof of Concept

Always create a minimal PoC:

```python
# Example PoC structure
import requests

url = "https://target.com/vulnerable/endpoint"
payload = {"param": "malicious_input"}

response = requests.post(url, json=payload)
print(f"Status: {response.status_code}")
print(f"Response: {response.text}")
```

### Impact Assessment

Rate the impact:
- **Critical**: Full system compromise, data breach
- **High**: Sensitive data access, privilege escalation
- **Medium**: Limited data access, partial control
- **Low**: Information disclosure, minor issues

## Phase 5: Reporting

### Report Structure

1. **Title**: Clear and descriptive
2. **Severity**: CVSS score and rating
3. **Description**: What the vulnerability is
4. **Steps to Reproduce**: Detailed walkthrough
5. **Impact**: What an attacker can do
6. **Proof of Concept**: Screenshots, videos, code
7. **Remediation**: Suggested fixes
8. **References**: CVEs, articles, resources

### Report Template

```markdown
# Vulnerability Title

## Severity
Critical / High / Medium / Low

## Description
Brief description of the vulnerability

## Steps to Reproduce
1. Step one
2. Step two
3. Step three

## Impact
What an attacker can achieve

## Proof of Concept
[Screenshots/Code/Video]

## Remediation
How to fix the issue

## References
- [Link 1](url)
- [Link 2](url)
```

## Best Practices

✅ **Do**:
- Test thoroughly and systematically
- Document everything
- Respect scope and rules
- Report responsibly
- Stay updated with new techniques

❌ **Don't**:
- Access real user data
- Cause denial of service
- Test out of scope
- Disclose publicly before fix
- Automate destructively

## Tools Arsenal

### Reconnaissance
- Subfinder, Amass, Assetfinder
- httpx, Nuclei, Naabu

### Scanning
- Burp Suite Professional
- Nuclei, Nmap, Nikto

### Exploitation
- SQLMap, XSStrike, Commix
- Custom Python scripts

### Reporting
- Markdown editors
- Screenshot tools
- Video recording software

## Continuous Learning

- Read disclosed reports
- Follow security researchers
- Practice on CTF platforms
- Attend conferences and webinars
- Contribute to open-source tools