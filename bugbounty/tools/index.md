---
layout: page
title: "Bug Bounty Tools"
subtitle: "Professional toolkit organized by offensive security specialties"
permalink: /bugbounty/tools/
---

## Bug Bounty Toolkit

A curated collection of tools and frameworks organized by domain specialty. Click on any card to view detailed definitions, brute-forcing scripts, and usage command sheets.

<div class="cards-grid">

  <div class="card my-repo-card">
    <div class="card-icon">🛠️</div>
    <h3 class="card-title">My Repo</h3>
    <p class="card-description">
      In-house custom tools and automation scripts including <strong>Vulntrace</strong> (dynamic vulnerability tracer), <strong>Kali Master</strong> (auto-provisioner), and <strong>Lab Manager</strong> (local orchestration).
    </p>
    <a href="{{ '/bugbounty/tools/my-repo/' | relative_url }}" class="card-link">View Custom Tools →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔍</div>
    <h3 class="card-title">Reconnaissance</h3>
    <p class="card-description">
      Passive and active asset harvesting tools like <strong>Subfinder</strong>, <strong>OWASP Amass</strong>, and <strong>Naabu</strong> to sweep domains and discover open service ports.
    </p>
    <a href="{{ '/bugbounty/tools/recon/' | relative_url }}" class="card-link">View Recon Tools →</a>
  </div>

  <div class="card">
    <div class="card-icon">📂</div>
    <h3 class="card-title">Fuzzing & Inputs</h3>
    <p class="card-description">
      Directory brute-forcing, JSON API fuzzing, and parameter discovery tools including <strong>FFUF</strong>, <strong>Gobuster</strong>, <strong>Arjun</strong>, and <strong>x8</strong>.
    </p>
    <a href="{{ '/bugbounty/tools/fuzzing/' | relative_url }}" class="card-link">View Fuzzing Tools →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔬</div>
    <h3 class="card-title">Vulnerability Scanners</h3>
    <p class="card-description">
      Automated configuration checkers and signature engines like <strong>Nuclei</strong> (YAML templates), <strong>Nikto</strong> web scanner, and <strong>Nmap NSE scripts</strong>.
    </p>
    <a href="{{ '/bugbounty/tools/scanners/' | relative_url }}" class="card-link">View Scanners →</a>
  </div>

  <div class="card">
    <div class="card-icon">⚡</div>
    <h3 class="card-title">Web Exploitation</h3>
    <p class="card-description">
      Database extractor and injection tools including <strong>SQLMap</strong> (automated SQLi), <strong>XSStrike</strong> (context XSS), <strong>Commix</strong> (command injection), and Burp Suite extensions.
    </p>
    <a href="{{ '/bugbounty/tools/web-exploitation/' | relative_url }}" class="card-link">View Exploitation Tools →</a>
  </div>

</div>