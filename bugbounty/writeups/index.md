---
layout: page
title: "Bug Bounty: Real-World Writeups"
subtitle: "Vulnerability writeups and reporting templates from live operations"
permalink: /bugbounty/writeups/
---

## Real-World Security Disclosures

A curated collection of real-world bug bounty writeups. These reports detail the vulnerabilities discovered, step-by-step reproduction steps, technical impact, and lessons learned. All writeups have been published after responsible disclosure and with explicit permission.

### Writeup Catalog

<div class="vertical-cards-grid" style="display: flex; flex-direction: column; gap: var(--spacing-md); max-width: 800px; margin: var(--spacing-xl) 0;">

  <!-- Writeup Template -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border: 1px dashed var(--border-color);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">📄</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Standard Writeup Template</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        Use this clean Markdown template to document, report, and disclose bugs professionally on HackerOne/Bugcrowd.
      </p>
    </div>
    <a href="{{ '/bugbounty/writeups/_template.md' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">View Template →</a>
  </div>

  <!-- RCE Writeup -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-danger);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">⚡</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">RCE on target.com via Unvalidated File Upload</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        <span class="badge badge-danger">Critical (9.8)</span> Leaking system access by bypassing filename extensions filter to execute an interactive web shell.
      </p>
    </div>
    <a href="{{ '/bugbounty/writeups/file-upload-rce/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">Read Report →</a>
  </div>

  <!-- IDOR Writeup -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-warning);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🔑</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">Full Account Takeover via IDOR in User Settings API</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        <span class="badge badge-warning">High (8.5)</span> Exploiting predictable UUID formats inside target's JSON API endpoint to reset password parameters.
      </p>
    </div>
    <a href="{{ '/bugbounty/writeups/idor-account-takeover/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">Read Report →</a>
  </div>

  <!-- SSRF Writeup -->
  <div class="card" style="display: flex; align-items: center; gap: var(--spacing-md); padding: var(--spacing-md); border-left: 3px solid var(--accent-danger);">
    <div class="card-icon" style="font-size: 2rem; margin-bottom: 0;">🌩️</div>
    <div style="flex-grow: 1;">
      <h3 class="card-title" style="margin-bottom: 2px;">SSRF on PDF Generator leaking AWS IAM Credentials</h3>
      <p class="card-description" style="margin-bottom: 0; font-size: 0.9rem;">
        <span class="badge badge-danger">Critical (9.1)</span> Bypassing SSRF local filters using DNS rebinding attacks to read internal cloud metadata routes.
      </p>
    </div>
    <a href="{{ '/bugbounty/writeups/ssrf-aws-leak/' | relative_url }}" class="btn btn-secondary" style="padding: 6px 12px; font-size: 0.85rem; flex-shrink: 0; text-decoration: none;">Read Report →</a>
  </div>

</div>

---

### 🔗 Back to Hub
- [Return to Bug Bounty Hub]({{ '/bugbounty/' | relative_url }})
