---
layout: page
title: "Offensive Security Tools"
subtitle: "Professional toolkit organized by cybersecurity specialties"
permalink: /tools/
---

## Offensive Security Toolkit

A centralized index of custom-developed utilities, configurations, and industry-standard security tools mapped to security specialties.

<div class="cards-grid">

  <!-- Special myrepo Card -->
  <div class="card my-repo-card" style="border: 2px solid var(--accent-primary);">
    <div class="card-icon">🛠️</div>
    <h3 class="card-title">myrepo (مايريبو)</h3>
    <p class="card-description">
      In-house custom tools and developer automations including <strong>Vulntrace</strong> (syscall tracer), <strong>Kali Master</strong>, and <strong>Lab Manager</strong>.
    </p>
    <a href="{{ '/tools/my-repo/' | relative_url }}" class="card-link">Explore My Repo →</a>
  </div>

  <div class="card">
    <div class="card-icon">🌐</div>
    <h3 class="card-title">Reconnaissance & OSINT</h3>
    <p class="card-description">
      Passive footprinting and active service mapping tools (Shodan, Naabu, Nmap, RustScan).
    </p>
    <a href="{{ '/tools/recon-osint/' | relative_url }}" class="card-link">Explore Recon & OSINT →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔍</div>
    <h3 class="card-title">Subdomain Enumeration & DNS</h3>
    <p class="card-description">
      Subdomain harvesting and active DNS resolution (Subfinder, Amass, Shuffledns, Massdns).
    </p>
    <a href="{{ '/tools/subdomain-dns/' | relative_url }}" class="card-link">Explore Subdomains & DNS →</a>
  </div>

  <div class="card">
    <div class="card-icon">🕸️</div>
    <h3 class="card-title">Web Application Security</h3>
    <p class="card-description">
      Path fuzzing, tech fingerprinting, and script parsing (Nuclei, FFUF, Gobuster, Arjun, x8).
    </p>
    <a href="{{ '/tools/web-security/' | relative_url }}" class="card-link">Explore Web Security →</a>
  </div>

  <div class="card">
    <div class="card-icon">💉</div>
    <h3 class="card-title">Vulnerability Exploitation</h3>
    <p class="card-description">
      Automating SQL injection, command execution, and XSS checks (SQLMap, XSStrike, Commix).
    </p>
    <a href="{{ '/tools/vuln-exploitation/' | relative_url }}" class="card-link">Explore Exploitation →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔐</div>
    <h3 class="card-title">Authentication & Session</h3>
    <p class="card-description">
      Audit credentials rate limiting and session tokens (Hydra, Medusa, jwt_tool).
    </p>
    <a href="{{ '/tools/auth-session/' | relative_url }}" class="card-link">Explore Auth & Session →</a>
  </div>

  <div class="card">
    <div class="card-icon">🏹</div>
    <h3 class="card-title">Network Penetration Testing</h3>
    <p class="card-description">
      Ethernet MITM, sniffing, WiFi auditing, and tunnel proxies (Bettercap, Responder, Hashcat).
    </p>
    <a href="{{ '/tools/network-pentest/' | relative_url }}" class="card-link">Explore Network Pentest →</a>
  </div>

  <div class="card">
    <div class="card-icon">🖥️</div>
    <h3 class="card-title">Post-Exploitation & Red Team</h3>
    <p class="card-description">
      C2 frameworks, lateral movement, and local checks (Sliver, Metasploit, WinPEAS, Mimikatz).
    </p>
    <a href="{{ '/tools/post-exploitation/' | relative_url }}" class="card-link">Explore Post-Exploitation →</a>
  </div>

  <div class="card">
    <div class="card-icon">🌩️</div>
    <h3 class="card-title">Cloud Security</h3>
    <p class="card-description">
      Audit cloud configurations, IAM access, and exposed buckets (Pacu, ROADtools, ScoutSuite).
    </p>
    <a href="{{ '/tools/cloud-security/' | relative_url }}" class="card-link">Explore Cloud Security →</a>
  </div>

  <div class="card">
    <div class="card-icon">🐛</div>
    <h3 class="card-title">Bug Bounty Specific Tools</h3>
    <p class="card-description">
      Automation pipelines, subdomain takeover, and reporting (ReconFTW, Subjack, Pwndoc).
    </p>
    <a href="{{ '/tools/bugbounty-specific/' | relative_url }}" class="card-link">Explore Bug Bounty Tools →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔬</div>
    <h3 class="card-title">Reverse Engineering</h3>
    <p class="card-description">
      Decompilers, debuggers, static analysis, and malware sandboxes (Ghidra, IDA, x64dbg).
    </p>
    <a href="{{ '/tools/reverse-engineering/' | relative_url }}" class="card-link">Explore Reverse Engineering →</a>
  </div>

  <div class="card">
    <div class="card-icon">🏁</div>
    <h3 class="card-title">CTF Tools</h3>
    <p class="card-description">
      Crypto, stego, forensics, and binary exploitation (CyberChef, Volatility, pwntools).
    </p>
    <a href="{{ '/tools/ctf-utils/' | relative_url }}" class="card-link">Explore CTF Tools →</a>
  </div>

  <div class="card">
    <div class="card-icon">🛡️</div>
    <h3 class="card-title">Active Directory</h3>
    <p class="card-description">
      Domain path sweeps and Windows network testing (BloodHound, Impacket, CrackMapExec).
    </p>
    <a href="{{ '/tools/active-directory/' | relative_url }}" class="card-link">Explore Active Directory →</a>
  </div>

  <div class="card">
    <div class="card-icon">📱</div>
    <h3 class="card-title">Mobile Security</h3>
    <p class="card-description">
      Decompilation and dynamic hooks on Android/iOS (MobSF, APKTool, Frida, objection).
    </p>
    <a href="{{ '/tools/mobile-security/' | relative_url }}" class="card-link">Explore Mobile Security →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔧</div>
    <h3 class="card-title">Proxy & Interception</h3>
    <p class="card-description">
      Interception web proxies, request encoders, and debuggers (Burp Suite, OWASP ZAP, Caido).
    </p>
    <a href="{{ '/tools/proxy-interception/' | relative_url }}" class="card-link">Explore Proxy & Interception →</a>
  </div>

  <div class="card">
    <div class="card-icon">🧰</div>
    <h3 class="card-title">General Purpose Utilities</h3>
    <p class="card-description">
      Terminal multiplexers, JSON formatters, and piping scripts (CyberChef, tmux, jq, anew).
    </p>
    <a href="{{ '/tools/general-utilities/' | relative_url }}" class="card-link">Explore Utilities →</a>
  </div>

</div>

---

### 📊 Quick Reference Matrix

| Category | Top Tool | Runner-up |
|----------|----------|-----------|
| Subdomain Enum | Subfinder | Amass |
| Port Scanning | Nmap | RustScan |
| Web Fuzzing | ffuf | Feroxbuster |
| Vuln Scanning | Nuclei | Jaeles |
| SQLi | SQLmap | Ghauri |
| XSS | Dalfox | XSStrike |
| C2 Framework | Cobalt Strike | Havoc |
| Disassembler | IDA Pro | Ghidra |
| Debugger | x64dbg | pwntbg |
| Memory Forensics | Volatility | Autopsy |
| Pwn | pwntools | GEF |
| Password Cracking | Hashcat | John |
| AD Attacks | BloodHound | Impacket |
| Mobile | MobSF | Frida |
| Proxy | Burp Suite | Caido |
