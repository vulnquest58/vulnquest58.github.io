---
layout: page
title: "Specialty Guide: Fuzzing & Parameter Discovery"
subtitle: "Tools for directory brute-forcing, API fuzzing, and input discovery"
permalink: /tools/fuzzing/
---

## 📂 Fuzzing & Parameter Discovery

Fuzzing and parameter discovery allow penetration testers to map hidden routes, variables, and administrative files that are not visible in standard web links.

### Tool Catalog

Select a tool below to view detailed specifications, mechanics, and cheatsheet commands.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">⚡</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">FFUF</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        An extremely fast, multi-threaded web fuzzer in Go designed for path, directory, vhost, and JSON parameter fuzzing.
      </p>
    </div>
    <a href="{{ '/tools/fuzzing/ffuf/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">📂</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Gobuster</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        A robust, high-performance brute-forcer written in Go for directories, files, DNS subdomains, and virtual hosts.
      </p>
    </div>
    <a href="{{ '/tools/fuzzing/gobuster/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🔑</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Arjun</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        HTTP parameter discovery suite utilizing smart batch querying and binary splits to quickly find hidden query inputs.
      </p>
    </div>
    <a href="{{ '/tools/fuzzing/arjun/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2.2rem; margin-bottom: 0;">🚀</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">x8</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        An ultra-fast Rust-based utility optimized for large wordlist parameter scans and custom HTTP header discovery.
      </p>
    </div>
    <a href="{{ '/tools/fuzzing/x8/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
