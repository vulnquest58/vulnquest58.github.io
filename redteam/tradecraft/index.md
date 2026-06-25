---
layout: page
title: Red Team Tradecraft
subtitle: AV/EDR evasion techniques and offensive tradecraft
permalink: /redteam/tradecraft/
---

## Tradecraft & Evasion Research

Modern red team operations require bypassing EDR solutions, AV engines, and behavioral monitoring stacks.

| Detection Layer | Bypass Strategy |
|---|---|
| Static Signature Scanning | Obfuscation, entropy reduction, custom PE packers |
| AMSI Script Scanning | AMSI patching via reflection, alternative runtimes |
| ETW Event Tracing | Unhooking ETW provider, syscall patching |
| API Hooking (Userland) | Direct/Indirect syscalls, fresh NTDLL mapping |
| Kernel Callbacks | BYOVD (Bring Your Own Vulnerable Driver) |

## NTDLL Userland Unhooking

EDRs insert ``jmp`` hooks into NTDLL function prologues. We bypass by loading a clean ntdll from disk.

## Direct Syscalls (HellsGate)

Invoke NT system calls directly with the correct SSN, bypassing all userland hooks.

## AMSI Bypass

Patch ``AmsiScanBuffer`` to return ``E_INVALIDARG`` via ``VirtualProtect``.

## Sleep Obfuscation (Ekko)

Encrypt agent memory during sleep using APC timers so memory scanners find only ciphertext.

## Nim Loader with Shellcode Encryption

Build loaders in Nim using AES-256 encrypted shellcode, executed via ``EnumSystemLocalesA`` callbacks.

## ETW Patching

Blind EDR telemetry by patching ``ntdll!EtwEventWrite`` to ``ret`` immediately.

> All techniques are for authorized engagements and security research only.
