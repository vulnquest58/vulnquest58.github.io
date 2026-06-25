---
layout: page
title: CTF Writeups Chronological List
subtitle: Timeline of all CTF writeups and solutions
description: "Chronological listing of all capture the flag (CTF) machine writeups and challenge walkthroughs."
---

## CTF Writeups Timeline

A complete chronological record of CTF challenges and machines solved, with detailed walkthough links and core vulnerability focuses.

<div class="timeline">

  <div class="timeline-item">
    <div class="timeline-date">February 2025</div>
    <div class="timeline-content">
      <h3><a href="{{ '/ctf/platforms/portswigger/' | relative_url }}">PortSwigger Web Academy - Web Cache Poisoning</a></h3>
      <p><span class="badge badge-warning">Web</span> Poisoning varnish/nginx caches utilizing unkeyed headers and path parameters to deliver XSS.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">November 2024</div>
    <div class="timeline-content">
      <h3><a href="{{ '/ctf/platforms/tryhackme/' | relative_url }}">TryHackMe - Wreath Network Pivot</a></h3>
      <p><span class="badge badge-danger">Network</span> Building multi-hop chisel tunnels and configuring proxychains to compromise internal domains.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">June 2024</div>
    <div class="timeline-content">
      <h3><a href="{{ '/ctf/platforms/hackthebox/' | relative_url }}">HackTheBox - Active Machine Walkthrough</a></h3>
      <p><span class="badge badge-info">Active Directory</span> Explited Group Policy Preferences (GPP) password leaks and executed Kerberoasting to escalate to Domain Admin.</p>
    </div>
  </div>

  <div class="timeline-item">
    <div class="timeline-date">March 2024</div>
    <div class="timeline-content">
      <h3><a href="{{ '/ctf/challenges/' | relative_url }}">Defcon Quals - Rop-Master Pwn Challenge</a></h3>
      <p><span class="badge badge-dark">Binary</span> Crafted a ROP chain bypassing DEP/ASLR on x86_64 ELF using ret2libc execution payload.</p>
    </div>
  </div>

</div>
