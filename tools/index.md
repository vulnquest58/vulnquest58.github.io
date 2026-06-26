---
layout: page
title: "Offensive Security Tools"
subtitle: "Professional toolkit organized by cybersecurity domains"
permalink: /tools/
---

## Offensive Security Toolkit

A centralized index of custom developed utilities, configurations, and industry-standard security tools mapped to security specialties.

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
    <div class="card-icon">🔍</div>
    <h3 class="card-title">Information Gathering</h3>
    <p class="card-description">
      Active and passive target footprinting, subdomain harvesting, and port discovery tools like <strong>Subfinder</strong>, <strong>Amass</strong>, and <strong>Naabu</strong>.
    </p>
    <a href="{{ '/tools/information-gathering/' | relative_url }}" class="card-link">Explore Info Gathering →</a>
  </div>

  <div class="card">
    <div class="card-icon">📂</div>
    <h3 class="card-title">Fuzzing & Inputs</h3>
    <p class="card-description">
      Directory brute-forcing, JSON API fuzzing, and parameter discovery tools including <strong>FFUF</strong>, <strong>Gobuster</strong>, <strong>Arjun</strong>, and <strong>x8</strong>.
    </p>
    <a href="{{ '/tools/fuzzing/' | relative_url }}" class="card-link">Explore Fuzzing Tools →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔬</div>
    <h3 class="card-title">Vulnerability Scanning</h3>
    <p class="card-description">
      Automated configuration check engines and vulnerability search templates like <strong>Nuclei</strong> (YAML rules), <strong>Nikto</strong>, and <strong>Nmap NSE scripts</strong>.
    </p>
    <a href="{{ '/tools/scanners/' | relative_url }}" class="card-link">Explore Scanners →</a>
  </div>

  <div class="card">
    <div class="card-icon">⚡</div>
    <h3 class="card-title">Web Application Exploitation</h3>
    <p class="card-description">
      Vulnerability verification and payload engines including <strong>SQLMap</strong> (database extraction), <strong>XSStrike</strong> (XSS context), and <strong>Commix</strong>.
    </p>
    <a href="{{ '/tools/web-exploitation/' | relative_url }}" class="card-link">Explore Exploitation →</a>
  </div>

  <!-- Direct Github Card -->
  <div class="card" style="border: 1px dashed var(--border-color);">
    <div class="card-icon"><i class="fab fa-github"></i></div>
    <h3 class="card-title">Developer GitHub</h3>
    <p class="card-description">
      Direct access to the source code repository on my GitHub account. Follow updates, submit pull requests, or fork tools.
    </p>
    <a href="https://github.com/vulnquest58" target="_blank" class="card-link">Visit GitHub Profile →</a>
  </div>

</div>
