---
layout: page
title: "Specialty Guide: Vulnerability Scanning"
subtitle: "Automated vulnerability scanning and security testing tools"
permalink: /tools/scanners/
---

## 🔬 Vulnerability Scanning (فحص الثغرات الآلي)

Vulnerability scanners automate the detection of configuration issues, open paths, known CVE signatures, and database/server vulnerabilities.

### Tool Catalog (أدوات فحص الثغرات)

Select a tool below to view detailed specifications, mechanics, and cheatsheet commands.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🎯</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Nuclei</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Highly customizable template-based vulnerability engine in Go. Leverages community YAML files to hunt complex CVEs.
      </p>
    </div>
    <a href="{{ '/tools/scanners/nuclei/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">💽</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Nikto</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Classic open-source web server scanning framework in Perl that audits configuration, directories, and default scripts.
      </p>
    </div>
    <a href="{{ '/tools/scanners/nikto/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🛡️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Nmap NSE</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Nmap Scripting Engine leveraging Lua scripts to run network vulnerability discovery alongside standard port sweeps.
      </p>
    </div>
    <a href="{{ '/tools/scanners/nmap/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
