---
layout: page
title: "Specialty Guide: Information Gathering"
subtitle: "Tools for passive and active asset discovery"
permalink: /tools/information-gathering/
---

## 🔍 Information Gathering (جمع المعلومات)

Information gathering is the first stage of any offensive security engagement. It focuses on finding domains, subdomains, open service ports, and the overall external footprint of the target.

### Tool Catalog (أدوات جمع المعلومات)

Select a tool below to view detailed specifications, mechanics, and cheatsheet commands.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🧭</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Subfinder</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Fast passive subdomain discovery engine that queries APIs to gather historical subdomain lists without active traffic.
      </p>
    </div>
    <a href="{{ '/tools/information-gathering/subfinder/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🌐</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">OWASP Amass</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        In-depth asset mapping, active and passive subdomain collection, ASN correlation, and active DNS resolution.
      </p>
    </div>
    <a href="{{ '/tools/information-gathering/amass/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🎯</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Naabu</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        High-speed TCP/UDP port scanner leveraging raw sockets to quickly identify open service ports.
      </p>
    </div>
    <a href="{{ '/tools/information-gathering/naabu/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
