---
layout: page
title: "Bug Bounty Tools Collection"
subtitle: "Curated toolkit mapping bug hunting utilities to detailed usage wikis"
permalink: /bugbounty/tools-collection/
---

## 🧰 Bug Bounty Tools Collection

This catalog aggregates the principal security tools and utilities utilized across my bug hunting workflows. Each card links directly to its corresponding detailed reference wiki, command-line cheatsheet, and integration guide under the main `/tools/` directory.

---

### 🔍 Reconnaissance & Subdomain Enumeration
Tools used for passive discovery, DNS mapping, and domain asset harvesting.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">📡</div>
    <h3 class="card-title">Subfinder</h3>
    <p class="card-description">
      Fast passive subdomain discovery tool querying dozens of public certificate and API databases.
    </p>
    <a href="{{ '/tools/subdomain-dns/subfinder/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">🧬</div>
    <h3 class="card-title">OWASP Amass</h3>
    <p class="card-description">
      Deep network footprinting and active DNS enumeration mapping external asset relationships.
    </p>
    <a href="{{ '/tools/subdomain-dns/amass/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔌</div>
    <h3 class="card-title">Naabu</h3>
    <p class="card-description">
      Ultra-fast port scanning tool designed for bulk host sweeps and active service discovery.
    </p>
    <a href="{{ '/tools/recon-osint/naabu/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">🗺️</div>
    <h3 class="card-title">Nmap</h3>
    <p class="card-description">
      The standard network mapper for port scanning, operating system detection, and script auditing.
    </p>
    <a href="{{ '/tools/recon-osint/nmap/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

</div>

---

### 🕸️ Web Fuzzing & Parameter Discovery
Tools used to bruteforce web paths, analyze parameters, and audit web application inputs.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">🌀</div>
    <h3 class="card-title">FFUF</h3>
    <p class="card-description">
      Fast web fuzzer written in Go, optimized for directory discovery, host header fuzzing, and parameter sweeps.
    </p>
    <a href="{{ '/tools/web-security/ffuf/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">📂</div>
    <h3 class="card-title">Gobuster</h3>
    <p class="card-description">
      URI path and DNS brute-forcer designed to locate hidden files and directories on target web servers.
    </p>
    <a href="{{ '/tools/web-security/gobuster/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">🎯</div>
    <h3 class="card-title">Arjun</h3>
    <p class="card-description">
      HTTP parameter discovery suite, locating hidden GET/POST variables with heuristic query engines.
    </p>
    <a href="{{ '/tools/web-security/arjun/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">⚡</div>
    <h3 class="card-title">x8</h3>
    <p class="card-description">
      Rust-based parameter and custom header discovery utility, built to find bypass mechanisms.
    </p>
    <a href="{{ '/tools/web-security/x8/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

</div>

---

### 🛡️ Vulnerability Scanners & Exploitation
Automating vulnerability audits, SQL injections, XSS detection, and remote system exploitation.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">🔬</div>
    <h3 class="card-title">Nuclei</h3>
    <p class="card-description">
      Fast, template-based vulnerability scanner automating checks using custom community YAML rules.
    </p>
    <a href="{{ '/tools/web-security/nuclei/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">🤖</div>
    <h3 class="card-title">Nikto</h3>
    <p class="card-description">
      Classic web server scanner auditing configurations, server software versions, and common server files.
    </p>
    <a href="{{ '/tools/web-security/nikto/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">💉</div>
    <h3 class="card-title">SQLMap</h3>
    <p class="card-description">
      The definitive database exploitation framework automating SQL injection detection and server takeovers.
    </p>
    <a href="{{ '/tools/vuln-exploitation/sqlmap/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">💥</div>
    <h3 class="card-title">XSStrike</h3>
    <p class="card-description">
      Advanced Cross-Site Scripting (XSS) detection suite equipped with smart payload parsing and filter bypasses.
    </p>
    <a href="{{ '/tools/vuln-exploitation/xsstrike/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card">
    <div class="card-icon">💻</div>
    <h3 class="card-title">Commix</h3>
    <p class="card-description">
      Command injection exploitation tool designed to find and automate shell creation in OS command injections.
    </p>
    <a href="{{ '/tools/vuln-exploitation/commix/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

</div>

---

### 🛠️ Custom In-House Tools & Repositories
Proprietary toolsets, syscall tracers, setup files, and provisioners.

<div class="cards-grid">

  <div class="card" style="border: 1px solid var(--accent-primary);">
    <div class="card-icon">👁️</div>
    <h3 class="card-title">Vulntrace</h3>
    <p class="card-description">
      Dynamic binary instrumentation trace framework monitoring memory leaks and API taint allocations.
    </p>
    <a href="{{ '/tools/vulntrace/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card" style="border: 1px solid var(--accent-primary);">
    <div class="card-icon">💻</div>
    <h3 class="card-title">Kali Master</h3>
    <p class="card-description">
      Automated configuration provisioner designed to rapidly build customized hacking environments.
    </p>
    <a href="{{ '/tools/kali-master/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

  <div class="card" style="border: 1px solid var(--accent-primary);">
    <div class="card-icon">📦</div>
    <h3 class="card-title">Lab Manager</h3>
    <p class="card-description">
      Docker and Vagrant provisioning infrastructure for orchestrating offline vulnerable labs.
    </p>
    <a href="{{ '/tools/lab-manager/' | relative_url }}" class="card-link">View Usage Wiki →</a>
  </div>

</div>

---

### 🔗 Back to Hub
- [Return to Bug Bounty Hub]({{ '/bugbounty/' | relative_url }})
