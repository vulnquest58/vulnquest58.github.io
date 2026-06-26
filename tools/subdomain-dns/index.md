---
layout: page
title: "Specialty Guide: Subdomain Enumeration & DNS"
subtitle: "Tools for mapping subdomains and DNS routing spaces"
permalink: /tools/subdomain-dns/
---

## 🔍 Subdomain Enumeration & DNS

Subdomain enumeration and DNS brute-forcing are critical steps to discover the hidden components of a target's infrastructure.

### Tool Catalog

Select a tool below to view detailed specifications, cheatsheets, or definitions.

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <!-- Detailed Wiki Tools -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🧭</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Subfinder</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Fast passive subdomain discovery tool leveraging public search API engines.
      </p>
    </div>
    <a href="{{ '/tools/subdomain-dns/subfinder/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-primary);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🌐</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">OWASP Amass</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Comprehensive active/passive subdomain mapper and DNS tracking framework.
      </p>
    </div>
    <a href="{{ '/tools/subdomain-dns/amass/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Wiki →</a>
  </div>

  <!-- Other Tools -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔎</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Assetfinder</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Lightweight Go tool to quickly discover domains and subdomains related to a target.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔀</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Shuffledns / Massdns</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        High-performance resolver engines designed to process millions of DNS queries using custom wordlists.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📡</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">DNSx</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        ProjectDiscovery's DNS resolution utility that allows bulk checking and brute force permutation.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔒</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Puredns</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Python/Go wrapper around massdns designed to filter out wildcards and false positives.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🌀</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Altdns / Gotator</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Subdomain permutation and alteration generator engines that create word combinations based on target structures.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📜</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">crt.sh</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        SSL/TLS certificate database scraper to identify hidden domains from old SSL registrations.
      </p>
    </div>
  </div>

  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">☁️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Chaos</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        ProjectDiscovery API dataset client offering pre-compiled lists of active internet domains.
      </p>
    </div>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/tools/' | relative_url }})
