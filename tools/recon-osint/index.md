---
layout: page
title: "Specialty Guide: Reconnaissance & OSINT"
subtitle: "Tools for passive footprinting and active target scans"
permalink: /tools/recon-osint/
---

## 🌐 Reconnaissance & OSINT (الاستطلاع والجمع المفتوح للبيانات)

This category focuses on information gathering and reconnaissance, split between passive footprinting and active network scanning.

### Tool Catalog (أدوات الاستطلاع)

Select a tool below to view detailed specifications, cheatsheets, or definitions.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <!-- Detailed Wiki Tools -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🎯</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Naabu</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        High-speed TCP/UDP port scanner utilizing raw socket sweeps to identify active service endpoints.
      </p>
    </div>
    <a href="{{ '/tools/recon-osint/naabu/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🛡️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Nmap</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Advanced network scanning, port enumeration, service fingerprinting, and Lua script-based audits.
      </p>
    </div>
    <a href="{{ '/tools/recon-osint/nmap/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <!-- Other Tools (Taxonomy Listings) -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🗺️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Maltego</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Graphical link analysis and relation mapping tool for mapping out digital footprints and open source intelligence.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔎</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Shodan / Censys / FOFA</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Search engines for internet-connected devices, certificates, exposing open ports, services, and vulnerabilities.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🦅</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">theHarvester</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        E-mail, subdomain, IP range, and employee name harvester querying public sources and search engines.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚙️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Recon-ng</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Full-featured Web Reconnaissance Framework written in Python with modular query API wrappers.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🕷️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">SpiderFoot</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Automated OSINT reconnaissance tool that queries hundreds of public databases to compile risk analysis heatmaps.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🕸️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">OSINT Framework</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Web directory cataloging free OSINT data sources organized by information type.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📜</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">crt.sh / certspotter</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        SSL/TLS Certificate Transparency logs scraping pipelines to harvest wildcards and subdomains.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚡</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Masscan</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Asynchronous TCP port scanner capable of scanning the entire Internet in under 6 minutes.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🦀</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">RustScan</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Fast modern port scanner written in Rust that integrates directly with Nmap for service detection.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🛰️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">DNSx / HTTPx</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Bulk multi-threaded DNS resolution and HTTP web server verification tools by ProjectDiscovery.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚔️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Katana / Gospider</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        High-performance web spiders and crawlers designed to parse client-side scripts and gather URL links.
      </p>
    </div>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
