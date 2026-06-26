---
layout: page
title: "Specialty Guide: Vulnerability Scanners"
subtitle: "Automated vulnerability scanning and security testing tools"
permalink: /bugbounty/tools/scanners/
---

## 🔬 Automated Vulnerability Scanners

Vulnerability scanners automate the detection of known CVEs, misconfigurations, default credentials, and common vulnerabilities. Select an active tool below to access definitions, mechanics, and cheatsheet commands.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">🎯</div>
    <h3 class="card-title">Nuclei</h3>
    <p class="card-description">
      Highly customizable template-based vulnerability engine in Go. Leverages community YAML files to hunt complex CVEs.
    </p>
    <a href="{{ '/bugbounty/tools/scanners/nuclei/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">💽</div>
    <h3 class="card-title">Nikto</h3>
    <p class="card-description">
      Classic open-source web server scanning framework in Perl that audits configuration, directories, and default scripts.
    </p>
    <a href="{{ '/bugbounty/tools/scanners/nikto/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">🛡️</div>
    <h3 class="card-title">Nmap NSE</h3>
    <p class="card-description">
      Nmap Scripting Engine leveraging Lua scripts to run network vulnerability discovery alongside standard port sweeps.
    </p>
    <a href="{{ '/bugbounty/tools/scanners/nmap/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/bugbounty/tools/' | relative_url }})
