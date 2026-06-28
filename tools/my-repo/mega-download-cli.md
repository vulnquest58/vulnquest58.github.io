---
layout: page
title: "mega-download-cli"
subtitle: "Batch MEGA downloader — smart selection, HackMyVM integration, auto-MEGA-CMD installer"
permalink: /tools/my-repo/mega-download-cli/
tool_type: cli
language: Python
status: active
github: https://github.com/vulnquest58/mega-download-cli
---

<!-- TOOL HEADER CARD -->
<div style="background:linear-gradient(135deg,rgba(59,130,246,0.06) 0%,rgba(124,58,237,0.04) 100%);border:1px solid rgba(59,130,246,0.3);border-radius:14px;padding:1.5rem;margin-bottom:2rem;">
  <div style="display:flex;align-items:center;gap:1rem;flex-wrap:wrap;">
    <div style="width:52px;height:52px;background:rgba(59,130,246,0.12);border:1px solid rgba(59,130,246,0.3);border-radius:10px;display:flex;align-items:center;justify-content:center;font-size:1.8rem;flex-shrink:0;">📥</div>
    <div>
      <h2 style="margin:0;font-size:1.3rem;">mega-download-cli</h2>
      <p style="margin:0;color:var(--text-muted);font-size:0.85rem;font-family:var(--font-mono);">Python · CLI · MEGA-CMD · Cross-Platform</p>
    </div>
    <div style="margin-left:auto;">
      <a href="https://github.com/vulnquest58/mega-download-cli" target="_blank" class="btn btn-secondary" style="font-size:0.8rem;padding:6px 14px;">
        <i class="fab fa-github"></i> GitHub
      </a>
    </div>
  </div>
  <div style="display:flex;gap:6px;flex-wrap:wrap;margin-top:1rem;">
    <span style="background:rgba(59,130,246,0.12);color:#93c5fd;border:1px solid rgba(59,130,246,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;font-family:var(--font-mono);">Python 3.8+</span>
    <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">Windows · Linux · macOS</span>
    <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">MEGA-CMD</span>
    <span style="background:rgba(220,38,38,0.12);color:#f87171;border:1px solid rgba(220,38,38,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">HackMyVM</span>
    <span style="background:rgba(234,179,8,0.12);color:#fbbf24;border:1px solid rgba(234,179,8,0.3);padding:2px 8px;border-radius:4px;font-size:0.75rem;">stdlib only</span>
  </div>
</div>

## What is mega-download-cli?

`mega-download-cli` is a cross-platform batch downloader for MEGA links. It wraps MEGA-CMD's non-interactive `mega-get` client to provide smart selection, live progress bars, parallel workers, and a direct HackMyVM machine resolution mode — all without touching a browser.

If MEGA-CMD is not installed, it **detects the situation and handles installation automatically**.

---

## Requirements

**Core mode** (batch download from links file): **zero external dependencies** — pure Python stdlib.

**`--hmv` mode** (HackMyVM integration):

```bash
pip install requests beautifulsoup4 rich
```

MEGA-CMD is handled automatically:

| OS | Auto-install method |
|----|---------------------|
| **Linux** | `apt install megacmd` → fallback `snap install megacmd` |
| **Windows** | Step-by-step guide + opens `https://mega.io/cmd` in browser |
| **macOS** | Opens download page in browser |

---

## Installation

```bash
git clone https://github.com/vulnquest58/mega-download-cli.git
cd mega-download-cli
```

No setup required. Run directly:

```bash
python mega_download.py --help
```

---

## Usage Guide

### 1 · Download all links from a file

```bash
python mega_download.py -f links.txt -d ~/Downloads/VMs
```

```
[INFO]  Platform         : Linux
[INFO]  MEGA-CMD         : mega-get  →  /usr/bin/mega-get
[INFO]  Links to fetch   : 5
────────────────────────────────────────────────────────────────────────────────

[1/5]  Milk  [Easy]  1.2 GB

Milk.zip                       |████████████████░░░░░░░░| 67.2%  1.21 GB/1.80 GB  45.3 MB/s  ETA: 0:00:13

[ OK ]  Done in 0:01:48.  Milk.zip  (1.80 GB)
────────────────────────────────────────────────────────────────────────────────

SUMMARY────────────────────────────────────────────────────────────────────────
  Total                5
  Succeeded            4
  Failed               1
  Elapsed              0:08:32
  Total downloaded     6.80 GB
```

### 2 · Interactive selection

```bash
python mega_download.py -f links.txt
```

```
────────────────────────────────────────────────────────────────────────────
#    Name                  Level     Size      URL
────────────────────────────────────────────────────────────────────────────
1    Milk                  Easy      1.2 GB    https://mega.nz/file/…
2    Calculator            Medium    2.1 GB    https://mega.nz/file/…
3    Nocturn               Hard      3.8 GB    https://mega.nz/file/…
4    Quick                 Easy      980 MB    https://mega.nz/file/…
────────────────────────────────────────────────────────────────────────────
Select which to download — e.g.  1  |  1,3,5  |  2-7  |  all
> 1,4
[INFO]  Selected 2 of 4 link(s).
```

### 3 · Select by index or range

```bash
python mega_download.py -f links.txt --select "1,3-5" -d ~/VMs
python mega_download.py -f links.txt --select "all" -d ~/VMs
```

### 4 · Filter by difficulty

```bash
python mega_download.py -f links.txt --level easy -d ~/VMs
python mega_download.py -f links.txt --level hard -d ~/VMs
```

### 5 · HackMyVM direct download

Resolve and download a HackMyVM machine **without a links file**:

```bash
# Via env vars (recommended)
export HMV_USER=yourusername
export HMV_PASS=yourpassword
python mega_download.py --hmv Calculator -d ~/VMs

# Via flags
python mega_download.py --hmv Calculator --hmv-user user --hmv-pass pass -d ~/VMs
```

```
[INFO]  Logging in to HackMyVM as 'yourusername'...
[ OK ]  Logged in.
[INFO]  Resolving download link for machine 'Calculator'...
[ OK ]  Resolved: https://mega.nz/file/XXXXXXXX#YYYYYYYY
[INFO]  Resolved 1 link for 'Calculator'.  Proceeding to download.
```

### 6 · List links without downloading

```bash
python mega_download.py -f links.txt --list
```

### 7 · Parallel downloads

```bash
python mega_download.py -f links.txt -j 3 -d ~/VMs
```

---

## links.txt Format

Auto-generated by [`vuln_hmv`](/tools/my-repo/vuln-hmv/) via `--save-links`. Can also be written manually:

```
# MachineName  [Easy]  1.2 GB
https://mega.nz/file/XXXXXXXX#YYYYYYYYY

# AnotherBox   [Hard]  3.7 GB
https://mega.nz/folder/XXXXXXXX#YYYYYYYYY
```

Comment lines (starting with `#`) define the name, difficulty, and size displayed in the selection table.

---

## Auto-install MEGA-CMD

When `mega-get` is not found on the system, the tool automatically:

**Linux** — tries to install via package manager:
```
[WARN]  MEGA-CMD (mega-get) was not found on this system.
  Attempting automatic installation of MEGA-CMD on Linux...
  [apt] Adding MEGA repository and installing megacmd...
[ OK ]  MEGA-CMD installed successfully via apt.
```

**Windows** — guides through manual install:
```
[WARN]  MEGA-CMD (mega-get) was not found on this system.

  MEGA-CMD is required for downloads.  Install steps:
  1) Download the installer from:  https://mega.io/cmd
  2) Run the MSI installer.
  3) Add  %LOCALAPPDATA%\MEGAcmd  to your PATH.
  4) Re-run this script.

  Open the download page now? [Y/n]:
```

---

## Options Reference

```
  -f FILE, --file FILE        Links file (default: links.txt)
  -d DIR,  --dest DIR         Destination directory (prompted if omitted)
  -j N,    --jobs N           Parallel workers (default: 1)
  --timeout SECS              Per-file timeout in seconds (default: 7200)
  --megacmd-dir DIR           Custom MEGA-CMD path (Windows only)
  --select SPEC               "1", "1,3,5", "2-7", "all"
  --level {easy,medium,hard}  Filter by difficulty
  --list                      Print link table and exit

HackMyVM integration:
  --hmv MACHINE               Machine name to resolve and download
  --hmv-user USER             HackMyVM username (or HMV_USER env var)
  --hmv-pass PASS             HackMyVM password (or HMV_PASS env var)
```

---

## Integration with vuln_hmv

The complete automation pipeline:

```bash
# ── Step 1: install vuln_hmv ──────────────────────────────────────────────
git clone https://github.com/vulnquest58/vuln_hmv.git
cd vuln_hmv && ./setup.sh

# ── Step 2: set credentials ───────────────────────────────────────────────
export HMV_USER=yourusername
export HMV_PASS=yourpassword

# ── Step 3: export MEGA links for all machines not yet downloaded ──────────
vuln_hmv --save-links links.txt -d ~/VMs

# ── Step 4: batch download ─────────────────────────────────────────────────
python mega-download-cli/mega_download.py -f links.txt -d ~/VMs

# ── OR: one-liner for a single machine ────────────────────────────────────
python mega-download-cli/mega_download.py --hmv Milk -d ~/VMs
```

---

## Tech Stack

| Component | Detail |
|-----------|--------|
| **Core** | Python stdlib only — `subprocess`, `pathlib`, `threading`, `shutil` |
| **Progress** | Custom live bar via `sys.stdout.write` — no curses dependency |
| **HMV mode** | `importlib.util` to dynamically load `vuln_hmv` at runtime |
| **MEGA backend** | Wraps `mega-get.bat` (Windows) or `mega-get` (Linux/macOS) |
