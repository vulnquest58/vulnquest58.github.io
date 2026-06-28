---
layout: page
title: "mega-download-cli"
subtitle: "Batch MEGA downloader with HackMyVM integration and auto-MEGA-CMD installer"
permalink: /tools/my-repo/mega-download-cli/
tool_type: cli
language: Python
status: active
github: https://github.com/vulnquest58/mega-download-cli
---

<div class="tool-header-card" style="background:linear-gradient(135deg,rgba(15,160,70,0.06) 0%,rgba(59,130,246,0.04) 100%);border:1px solid rgba(15,160,70,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">
  <div style="display:flex;align-items:center;gap:1rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(59,130,246,0.12);border:1px solid rgba(59,130,246,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.8rem;flex-shrink:0;">📥</div>
    <div>
      <h2 style="margin:0;font-size:1.3rem;">mega-download-cli</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">Python · CLI · MEGA-CMD Automation</p>
    </div>
    <div style="margin-left:auto;display:flex;gap:8px;flex-wrap:wrap;">
      <a href="https://github.com/vulnquest58/mega-download-cli" target="_blank" class="btn btn-secondary" style="font-size:0.8rem;padding:6px 14px;">
        <i class="fab fa-github"></i> GitHub
      </a>
    </div>
  </div>
  <div style="display:flex;gap:6px;flex-wrap:wrap;margin-top:1rem;">
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Python 3.8+</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Windows · Linux · macOS</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">MEGA-CMD</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">HackMyVM</span>
  </div>
</div>

## Overview

`mega-download-cli` is a cross-platform batch downloader for MEGA links built on top of MEGA-CMD's `mega-get` client. It features a live progress bar, smart selection, parallel workers, and a direct HackMyVM integration that resolves machine download links on the fly.

If MEGA-CMD is not installed, the tool **auto-installs it** — via `apt`/`snap` on Linux, or via guided browser download on Windows/macOS.

---

## Features

| Feature | Detail |
|---------|--------|
| 📥 **Batch download** | Download all MEGA links in a `links.txt` file |
| 📊 **Live progress bar** | Real-time speed, ETA, and downloaded size |
| 🎯 **Smart selection** | `--select "1,3-5"` or `--level easy/medium/hard` |
| 🎮 **HackMyVM mode** | `--hmv <MachineName>` downloads a HMV machine directly |
| 🔧 **Auto-installer** | Installs MEGA-CMD automatically if not found |
| 🔁 **Parallel workers** | `--jobs N` for concurrent downloads |
| 🗂️ **Failed log** | Saves failed URLs to `.mega_dl_logs/failed_links.txt` |

---

## Installation

```bash
git clone https://github.com/vulnquest58/mega-download-cli.git
cd mega-download-cli
pip install -r requirements.txt   # only needed for --hmv mode
```

No third-party libraries required for plain MEGA download mode (stdlib only).

---

## Usage

### Download from a links file

```bash
python mega_download.py -f links.txt -d ~/Downloads/VMs
```

```
[INFO]  Platform         : Linux
[INFO]  MEGA-CMD         : mega-get  →  /usr/bin/mega-get
[INFO]  Links to fetch   : 5
────────────────────────────────────────────────────────────────────────────────

[1/5]  Milk  [Easy]

Milk.zip                       |████████████████░░░░░░░░| 67.2%  1.21 GB/1.80 GB  45.3 MB/s  ETA: 0:00:13

[ OK ]  Done in 0:01:48.  Milk.zip  (1.80 GB)
```

### HackMyVM direct download

```bash
export HMV_USER=yourusername
export HMV_PASS=yourpassword

python mega_download.py --hmv Calculator -d ~/VMs
```

```
[INFO]  Logging in to HackMyVM as 'yourusername'...
[ OK ]  Logged in.
[INFO]  Resolving download link for machine 'Calculator'...
[ OK ]  Resolved: https://mega.nz/file/...
[INFO]  Resolved 1 link for 'Calculator'.  Proceeding to download.
```

### Interactive selection

```bash
python mega_download.py -f links.txt
# Shows a numbered table, prompts for selection
# Press Enter to download all, or type: 1,3-5,8
```

### Filter by difficulty

```bash
python mega_download.py -f links.txt --level easy -d ~/VMs
```

---

## Auto-install MEGA-CMD

When `mega-get` is not found on the system:

| OS | Behavior |
|----|---------|
| **Linux** | Runs `apt install megacmd` → fallback `snap install megacmd` |
| **Windows** | Prints step-by-step guide + opens `https://mega.io/cmd` in browser |
| **macOS** | Opens download page in browser |

---

## Options Reference

```
-f FILE, --file FILE        Links file (default: links.txt)
-d DIR,  --dest DIR         Destination directory (prompted if omitted)
-j N,    --jobs N           Parallel workers (default: 1)
--timeout SECS              Per-file timeout (default: 7200s)
--megacmd-dir DIR           Custom MEGA-CMD path (Windows)
--select SPEC               e.g. "1", "1,3,5", "2-7", "all"
--level {easy,medium,hard}  Filter by difficulty
--list                      Print link table and exit

HackMyVM integration:
--hmv MACHINE               Machine name to resolve and download
--hmv-user USER             Username (or HMV_USER env var)
--hmv-pass PASS             Password (or HMV_PASS env var)
```

---

## links.txt Format

```
# MachineName  [Easy]  1.2 GB
https://mega.nz/file/XXXXXXXX#YYYYYYYYYYY

# AnotherBox   [Hard]  3.7 GB
https://mega.nz/folder/XXXXXXXX#YYYYYYYYYYY
```

Auto-generated by [`vuln_hmv`](/tools/my-repo/vuln-hmv/) via `--save-links`.

---

## Tech Stack

- **stdlib only** for core download: `subprocess`, `pathlib`, `threading`, `shutil`
- `requests` + `beautifulsoup4` + `rich` — only for `--hmv` HackMyVM integration
