---
layout: page
title: "Bug Bounty Hub"
subtitle: "Professional vulnerability hunting methodologies, writeups, and tools"
permalink: /bugbounty/
---

## Vulnerability Hunting Hub

Welcome to my Bug Bounty portal. Here you can explore my structured methodologies across different eras, read detailed writeups from real-world operations, and view the specialized tools catalog.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">📅</div>
    <h3 class="card-title">2024 Methodology</h3>
    <p class="card-description">
      Classic Bug Bounty. Focuses on passive subdomain harvesting, directory fuzzing, and traditional web injection flaws (SQLi, XSS, LFI).
    </p>
    <a href="{{ '/bugbounty/methodology/2024/' | relative_url }}" class="card-link">Explore 2024 Stages →</a>
  </div>

  <div class="card" style="border: 1px solid var(--accent-primary);">
    <div class="card-icon">🚀</div>
    <h3 class="card-title">2025 Methodology</h3>
    <p class="card-description">
      Modern Bug Bounty. Focuses on JavaScript analysis, GraphQL/REST API schema mapping, SSRF, IDOR, and automated SQLMap/XSStrike flows.
    </p>
    <a href="{{ '/bugbounty/methodology/2025/' | relative_url }}" class="card-link">Explore 2025 Stages →</a>
  </div>

  <div class="card" style="border: 2px solid var(--accent-primary); box-shadow: var(--shadow-glow);">
    <div class="card-icon">🛸</div>
    <h3 class="card-title">2026 Methodology</h3>
    <p class="card-description">
      Next-Gen Bug Bounty. Covers AI-driven discovery, multi-cloud S3/Blob sweeps, single-packet HTTP/2 race conditions, and WAF/EDR bypasses.
    </p>
    <a href="{{ '/bugbounty/methodology/2026/' | relative_url }}" class="card-link">Explore 2026 Stages →</a>
  </div>

  <div class="card">
    <div class="card-icon">📝</div>
    <h3 class="card-title">Writeups & Templates</h3>
    <p class="card-description">
      Detailed writeups of real-world bug bounty hunts showing step-by-step reproduction, and access to standard Markdown templates.
    </p>
    <a href="{{ '/bugbounty/writeups/' | relative_url }}" class="card-link">Browse Writeups →</a>
  </div>

  <div class="card">
    <div class="card-icon">🧰</div>
    <h3 class="card-title">Tools Collection</h3>
    <p class="card-description">
      A collection of all the tools utilized during my bug bounty operations, with links to their usage guides in the main Tools section.
    </p>
    <a href="{{ '/bugbounty/tools-collection/' | relative_url }}" class="card-link">View Tools Collection →</a>
  </div>

</div>