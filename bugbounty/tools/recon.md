---
layout: page
title: "Specialty Guide: Reconnaissance Tools"
subtitle: "Tools for passive and active asset discovery"
permalink: /bugbounty/tools/recon/
---

## 🔍 Attack Surface Discovery Tools

Reconnaissance is focused on finding hidden assets, IP spaces, and domains owned by the target organization.

---

## 🌐 1. Subfinder

### 📘 Definition
**Subfinder** is a fast, passive subdomain discovery tool built in Go. It queries various public, historical, and threat intelligence sources to harvest subdomain lists.

### 🧪 Passive Enumeration
Subfinder operates without sending any direct traffic to the target's servers. Instead, it interacts with APIs (such as VirusTotal, Shodan, Censys, SecurityTrails, and DNSDumpster) to collect records.

### 🚀 Usage & Common Commands
```bash
# Basic passive subdomain scan for a domain
subfinder -d target.com -o subdomains.txt

# Run scan using all available passive search engines and threads
subfinder -d target.com -all -t 50 -silent -o subdomains_all.txt
```

---

## 📡 2. OWASP Amass

### 📘 Definition
**Amass** is an in-depth asset mapping and domain tracking engine. It excels at active and passive subdomain collection, ASN correlation, and DNS resolution.

### 🧪 DNS Bruteforcing & Scraping
Amass uses advanced techniques like:
*   **Active Subdomain Bruteforcing**: Querying combinations of words from wordlists.
*   **DNS Alteration & Permutation**: Generating subdomains based on existing names (e.g. `dev.target.com` -> `dev-test.target.com`).
*   **Reverse DNS Sweeping**: Scanning IP ranges and resolving them back to hostnames.

### 🚀 Usage & Common Commands
```bash
# Passive subdomain enumeration
amass enum -passive -d target.com -o passive_subs.txt

# Active subdomain discovery including bruteforcing and IP sweeps
amass enum -active -d target.com -w /usr/share/seclists/Discovery/DNS/subdomains-top1million-110000.txt -o active_subs.txt

# ASN discovery to identify target's IP spaces
amass intel -org "Target Corp"
```

---

## 🎯 3. Naabu

### 📘 Definition
**Naabu** is a high-speed TCP/UDP port scanner written in Go. It is designed to quickly scan thousands of hosts to locate open service ports.

### 🧪 Active Packet Sweeping
Naabu utilizes raw socket parsing to perform SYN scans. It sends SYN packets to a list of target IPs/ports and listens for SYN-ACK or RST responses to identify open ports at lightning speed.

### 🚀 Usage & Common Commands
```bash
# Scan a list of domains for standard web ports
naabu -list subdomains.txt -p 80,443,8080,8443 -o open_ports.txt

# Full port scan (all 65,535 ports) on a target host
naabu -host target.com -p - -rate 1000 -o target_full_ports.txt
```
