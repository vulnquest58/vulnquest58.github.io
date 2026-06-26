---
layout: page
title: "Specialty Guide: Fuzzing & Parameter Discovery"
subtitle: "Tools for directory brute-forcing, API fuzzing, and input discovery"
permalink: /bugbounty/tools/fuzzing/
---

## 📂 Web Fuzzing & Input Discovery Tools

Fuzzing is the process of brute-forcing directories, URLs, parameters, and payloads to locate hidden files, administrative interfaces, and application variables. Select a tool from the list below to view deep usage guides and command templates.

<div class="cards-grid">

  <div class="card">
    <div class="card-icon">⚡</div>
    <h3 class="card-title">FFUF</h3>
    <p class="card-description">
      An extremely fast, multi-threaded web fuzzer in Go designed for path, directory, vhost, and JSON parameter fuzzing.
    </p>
    <a href="{{ '/bugbounty/tools/fuzzing/ffuf/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">📂</div>
    <h3 class="card-title">Gobuster</h3>
    <p class="card-description">
      A robust, high-performance brute-forcer written in Go for directories, files, DNS subdomains, and virtual hosts.
    </p>
    <a href="{{ '/bugbounty/tools/fuzzing/gobuster/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">🔑</div>
    <h3 class="card-title">Arjun</h3>
    <p class="card-description">
      HTTP parameter discovery suite utilizing smart batch querying and binary splits to quickly find hidden query inputs.
    </p>
    <a href="{{ '/bugbounty/tools/fuzzing/arjun/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

  <div class="card">
    <div class="card-icon">🚀</div>
    <h3 class="card-title">x8</h3>
    <p class="card-description">
      An ultra-fast Rust-based utility optimized for large wordlist parameter scans and custom HTTP header discovery.
    </p>
    <a href="{{ '/bugbounty/tools/fuzzing/x8/' | relative_url }}" class="card-link">View Wiki & Cheatsheet →</a>
  </div>

</div>

---

### 🔗 Back to Toolkit
- [Return to Main Tools Listing]({{ '/bugbounty/tools/' | relative_url }})
