---
layout: page
title: "Specialty Guide: Web Application Security"
subtitle: "Tools for directory fuzzing, tech fingerprinting, and script analysis"
permalink: /tools/web-security/
---

## 🕸️ Web Application Security (أمن تطبيقات الويب)

This category hosts scanning, directory brute-forcing, JavaScript analysis, and parameter parsing tools to evaluate vulnerabilities in web environments.

### Tool Catalog (أدوات أمن الويب)

Select a tool below to view detailed specifications, cheatsheets, or definitions.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <!-- Detailed Wiki Tools -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🎯</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Nuclei</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Highly customizable template-based YAML vulnerability scanner by ProjectDiscovery.
      </p>
    </div>
    <a href="{{ '/tools/web-security/nuclei/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">💽</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Nikto</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Classic Perl scanner to probe configuration settings and files on web servers.
      </p>
    </div>
    <a href="{{ '/tools/web-security/nikto/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚡</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">ffuf</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Ultra-fast web fuzzer in Go designed to brute-force URLs, paths, and headers.
      </p>
    </div>
    <a href="{{ '/tools/web-security/ffuf/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📂</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Gobuster</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Multi-threaded directory, file, VHost, and DNS brute-forcer.
      </p>
    </div>
    <a href="{{ '/tools/web-security/gobuster/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔑</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Arjun</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Heuristic HTTP parameter discovery suite mapping hidden endpoints inputs.
      </p>
    </div>
    <a href="{{ '/tools/web-security/arjun/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🚀</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">x8</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Rust-based parameter and custom header discovery utility.
      </p>
    </div>
    <a href="{{ '/tools/web-security/x8/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <!-- Other Tools -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🏷️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">WhatWeb / Wappalyzer / Webanalyze</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Offensive application technology profile fingerprinting engines identifying CMS, JS frameworks, and headers.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🛡️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">CMSeeK / WPScan</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Vulnerability scanners specialized in content management frameworks (WordPress, Joomla, Drupal).
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📂</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Feroxbuster / Dirsearch / wfuzz</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Advanced directory scanners and web application input fuzzer engines.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🕷️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">ParamSpider</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Mining URL parameter structures from archive indexes like Wayback.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📜</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">LinkFinder / JSFinder / SecretFinder</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        JavaScript static analysis scripts to harvest endpoints, API urls, and hardcoded API tokens.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🗃️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Trufflehog / Gitleaks</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Entropy scanners searching git repository history for leaked passwords and certificates.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔗</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Waybackurls / Gau / Katana</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        URL scanners and history index aggregators to collect all endpoints belonging to the target.
      </p>
    </div>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
