---
layout: page
title: "vuln_hmv"
subtitle: "Full-featured HackMyVM CLI — browse, download, submit flags"
permalink: /tools/my-repo/vuln-hmv/
tool_type: cli
language: Python
status: active
github: https://github.com/vulnquest58/vuln_hmv
---

<div class="tool-header-card" style="background:linear-gradient(135deg,rgba(15,160,70,0.06) 0%,rgba(59,130,246,0.04) 100%);border:1px solid rgba(15,160,70,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">
  <div style="display:flex;align-items:center;gap:1rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(15,160,70,0.12);border:1px solid rgba(15,160,70,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.8rem;flex-shrink:0;">🎮</div>
    <div>
      <h2 style="margin:0;font-size:1.3rem;">vuln_hmv</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">Python · CLI · HackMyVM Automation</p>
    </div>
    <div style="margin-left:auto;display:flex;gap:8px;flex-wrap:wrap;">
      <a href="https://github.com/vulnquest58/vuln_hmv" target="_blank" class="btn btn-secondary" style="font-size:0.8rem;padding:6px 14px;">
        <i class="fab fa-github"></i> GitHub
      </a>
    </div>
  </div>
  <div style="display:flex;gap:6px;flex-wrap:wrap;margin-top:1rem;">
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Python 3.8+</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">HackMyVM</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Web Scraper</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">MEGA Integration</span>
  </div>
</div>

## Overview

`vuln_hmv` is a command-line interface for [HackMyVM](https://hackmyvm.eu) that lets you browse machines, compare against your local library, resolve MEGA download links, submit flags, and view the leaderboard — all from the terminal without touching a browser.

Designed to work seamlessly alongside [`mega-download-cli`](/tools/my-repo/mega-download-cli/) for a complete VM download automation pipeline.

---

## Features

| Feature | Detail |
|---------|--------|
| 🖥️ **VM Browser** | Lists all machines with difficulty, size, creator, and solved status |
| 📂 **Local comparison** | Scans a local directory and marks which VMs are already downloaded |
| 📥 **Link resolver** | Resolves MEGA / Google Drive download links per machine |
| 💾 **Save links** | Exports undownloaded machine links to a `links.txt` for `mega-download-cli` |
| 🏆 **Leaderboard** | Top players ranked by points and machines solved |
| 🚩 **Flag submission** | Submit user/root flags from CLI |
| 🔬 **Challenges** | Browse all HackMyVM challenges with categories and difficulty |
| 🧪 **Labs** | View available lab environments |

---

## Installation

```bash
git clone https://github.com/vulnquest58/vuln_hmv.git
cd vuln_hmv
pip install -r requirements.txt
```

---

## Configuration

Credentials are read from environment variables — never hardcoded:

```bash
export HMV_USER=yourusername
export HMV_PASS=yourpassword
```

---

## Usage

### Browse all VMs

```bash
python script.py -v -d /path/to/local/vms
```

```
 ╔══════════════════════════════════════════════════════════════╗
 ║         HackMyVM CLI Tool - Complete Edition                  ║
 ╚══════════════════════════════════════════════════════════════╝

  #    Name          Level    Size     Creator     Status
  ──────────────────────────────────────────────────────────
  1    Milk          Easy     1.2 GB   tasiyanci   ✅ Downloaded
  2    Calculator    Medium   2.1 GB   tasiyanci   🔴 Missing
  3    Nocturn       Hard     3.8 GB   cromiphi    ⚡ To Hack
```

### Save links for batch download

```bash
python script.py --save-links links.txt -d ~/VMs
# Exports all "missing" machine MEGA links → links.txt
```

### Submit a flag

```bash
python script.py -s user.txt Milk
# ✅ CORRECT! Congratulations!
```

### Leaderboard

```bash
python script.py -l
```

---

## Integration

Works as the data source for [`mega-download-cli`](/tools/my-repo/mega-download-cli/):

```bash
# 1. Fetch unsolved machine links
python vuln_hmv/script.py --save-links links.txt -d ~/VMs

# 2. Batch download
python mega-download-cli/mega_download.py -f links.txt -d ~/VMs
```

---

## Tech Stack

- `requests` + `BeautifulSoup4` — scraping HackMyVM
- `rich` — terminal UI (tables, panels, progress)
- `concurrent.futures` — parallel link resolution
