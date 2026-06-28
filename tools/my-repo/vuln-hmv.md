---
layout: page
title: "vuln_hmv"
subtitle: "HackMyVM CLI — VM browser, link resolver, flag submitter, leaderboard"
permalink: /tools/my-repo/vuln-hmv/
tool_type: cli
language: Python
status: active
github: https://github.com/vulnquest58/vuln_hmv
---

<!-- TOOL HEADER CARD -->
<div style="background:linear-gradient(135deg,rgba(15,160,70,0.06) 0%,rgba(59,130,246,0.04) 100%);border:1px solid rgba(15,160,70,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">
  <div style="display:flex;align-items:center;gap:1rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(15,160,70,0.12);border:1px solid rgba(15,160,70,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.8rem;flex-shrink:0;">🎮</div>
    <div>
      <h2 style="margin:0;font-size:1.3rem;">vuln_hmv</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">Python · CLI · HackMyVM Automation</p>
    </div>
    <div style="margin-left:auto;">
      <a href="https://github.com/vulnquest58/vuln_hmv" target="_blank" class="btn btn-secondary" style="font-size:0.8rem;padding:6px 14px;">
        <i class="fab fa-github"></i> GitHub
      </a>
    </div>
  </div>
  <div style="display:flex;gap:6px;flex-wrap:wrap;margin-top:1rem;">
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">Python 3.8+</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Linux · macOS</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Web Scraper</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">MEGA Integration</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">HackMyVM</span>
  </div>
</div>

## What is vuln_hmv?

`vuln_hmv` is a terminal-first CLI for [HackMyVM](https://hackmyvm.eu) that replaces browser interaction entirely. It browses all published machines, compares them against your local VM library, resolves MEGA download links, submits flags, and shows the live leaderboard — in one unified command.

Works seamlessly as the data-source companion for [`mega-download-cli`](/tools/my-repo/mega-download-cli/).

---

## Installation

```bash
git clone https://github.com/vulnquest58/vuln_hmv.git
cd vuln_hmv
chmod +x setup.sh
./setup.sh
```

### What `setup.sh` does

| Step | Action |
|------|--------|
| ① | Verifies Python 3.8+ is present |
| ② | Installs `requests`, `beautifulsoup4`, `rich`, `urllib3` via pip |
| ③ | Copies `vuln_hmv.py` → `/usr/local/bin/vuln_hmv` with sudo |
| ④ | Makes it executable and patches the shebang |
| ⑤ | Confirms the command is available in `$PATH` |

After install, `vuln_hmv` is available **system-wide** as a shell command.

---

## Configuration

```bash
# Add to ~/.bashrc or ~/.zshrc
export HMV_USER=yourusername
export HMV_PASS=yourpassword
```

Credentials are **never stored in the script** — always read from environment variables.

---

## Usage Guide

### 1 · List all VMs

```bash
vuln_hmv -v
```

```
  ╔══════════════════════════════════════════════════════════════╗
  ║         HackMyVM CLI Tool - Complete Edition                  ║
  ║   VMs • Challenges • Leaderboard • Labs • Submit Flags       ║
  ╚══════════════════════════════════════════════════════════════╝

  #    Name          Level    Size     Creator        Status
  ──────────────────────────────────────────────────────────────
  1    Milk          Easy     1.2 GB   tasiyanci      ✅ Downloaded
  2    Calculator    Medium   2.1 GB   tasiyanci      🔴 Missing
  3    Nocturn       Hard     3.8 GB   cromiphi       ⚡ To Hack
  4    Quick         Easy     980 MB   sML            🔴 Missing
```

### 2 · List with local directory comparison

```bash
vuln_hmv -v -d /path/to/local/vms
```

Scans your directory for `.zip` / `.7z` files and automatically marks each VM as:
- ✅ **Downloaded** — archive present locally
- ⚡ **To Hack** — downloaded but flag not submitted
- 🔴 **Missing** — not yet downloaded

### 3 · Filter VMs

```bash
vuln_hmv -v --filter missing      # only VMs not yet downloaded
vuln_hmv -v --filter easy         # Easy difficulty only
vuln_hmv -v --filter tohacking    # downloaded but unsolved
```

### 4 · Save MEGA links for batch download

```bash
vuln_hmv --save-links links.txt -d ~/VMs
```

Resolves the MEGA link for every **missing** machine and writes them to `links.txt` in the format expected by `mega-download-cli`:

```
# Milk  [Easy]  1.2 GB
https://mega.nz/file/XXXXXXXX#YYYYYYY

# Quick  [Easy]  980 MB
https://mega.nz/file/XXXXXXXX#YYYYYYY
```

### 5 · Submit a flag

```bash
vuln_hmv -s user.txt Milk
# ✅ CORRECT! Congratulations!

vuln_hmv -s root.txt Milk
# ✅ CORRECT! Congratulations!
```

### 6 · Leaderboard

```bash
vuln_hmv -l
```

Shows top 50 players with rank, username, points, and machines solved.

### 7 · Browse challenges

```bash
vuln_hmv -c
```

### 8 · View labs

```bash
vuln_hmv --labs
```

---

## Options Reference

```
Mode selection (mutually exclusive):
  -v, --vms              List VMs with local comparison
  -c, --challenges       List all challenges
  -l, --leaderboard      Show leaderboard
  --labs                 Show HMV Labs
  -s FLAG VM             Submit a flag

VM mode options:
  -d DIR, --directory    Local VM directory for comparison
  -f, --filter           all | missing | tohacking | downloaded | easy | medium | hard
  --no-links             Skip MEGA link resolution (faster listing)
  --workers N            Threads for parallel link resolution (default: 10)
  --save-links [FILE]    Export MEGA links of missing machines (default: links.txt)
```

---

## Integration with mega-download-cli

The two tools form a complete VM acquisition pipeline:

```bash
# 1. Install both tools
git clone https://github.com/vulnquest58/vuln_hmv.git && cd vuln_hmv && ./setup.sh
git clone https://github.com/vulnquest58/mega-download-cli.git

# 2. Export links for all missing machines
vuln_hmv --save-links links.txt -d ~/VMs

# 3. Download them all via MEGA-CMD
python mega-download-cli/mega_download.py -f links.txt -d ~/VMs

# OR: download a specific machine in one command
python mega-download-cli/mega_download.py --hmv Milk -d ~/VMs
```

---

## Tech Stack

| Library | Role |
|---------|------|
| `requests` | HTTP session for HackMyVM auth and scraping |
| `beautifulsoup4` | HTML parsing for VM metadata extraction |
| `rich` | Terminal UI — tables, panels, progress bars |
| `concurrent.futures` | Parallel MEGA link resolution |
