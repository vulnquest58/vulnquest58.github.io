---
layout: page
title: CTF Solved Challenges
subtitle: Structured directory of capture the flag solutions
description: "Listing of specific CTF challenges solved across various categories like Web, Reverse Engineering, Pwn, and Cryptography."
---

## Challenge Directory

This page catalogs individual CTF challenges I have solved, categorized by focus area. These solutions highlight my technical methodology and approach to exploiting specific vulnerabilities.

<div class="category-section">
  <h3><i class="fas fa-globe"></i> Web Exploitation</h3>
  <table class="challenges-table">
    <thead>
      <tr>
        <th>Challenge Name</th>
        <th>Event / Platform</th>
        <th>Difficulty</th>
        <th>Core Concept</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>SQLi-Helper</td>
        <td>HackTheBox</td>
        <td>Medium</td>
        <td>Second-Order SQL Injection in PDF generator</td>
      </tr>
      <tr>
        <td>Smuggle-Gate</td>
        <td>PortSwigger</td>
        <td>Hard</td>
        <td>CL.TE Request Smuggling via TE header obfuscation</td>
      </tr>
      <tr>
        <td>JWT-Bypass</td>
        <td>TryHackMe</td>
        <td>Easy</td>
        <td>Symmetric key brute-forcing and claim modification</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="category-section">
  <h3><i class="fas fa-cogs"></i> Binary Exploitation & Pwn</h3>
  <table class="challenges-table">
    <thead>
      <tr>
        <th>Challenge Name</th>
        <th>Event / Platform</th>
        <th>Difficulty</th>
        <th>Core Concept</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Rop-Master</td>
        <td>Defcon Quals</td>
        <td>Hard</td>
        <td>ROP chain bypassing NX/ASLR using ret2libc</td>
      </tr>
      <tr>
        <td>Format-Fun</td>
        <td>HackTheBox</td>
        <td>Medium</td>
        <td>Format string vulnerability leading to GOT overwrite</td>
      </tr>
      <tr>
        <td>Stack-Over</td>
        <td>TryHackMe</td>
        <td>Easy</td>
        <td>Classic stack buffer overflow overriding EIP</td>
      </tr>
    </tbody>
  </table>
</div>

<div class="category-section">
  <h3><i class="fas fa-key"></i> Cryptography & Reverse Engineering</h3>
  <table class="challenges-table">
    <thead>
      <tr>
        <th>Challenge Name</th>
        <th>Event / Platform</th>
        <th>Difficulty</th>
        <th>Core Concept</th>
      </tr>
    </thead>
    <tbody>
      <tr>
        <td>Xor-Decrypt</td>
        <td>CryptoHack</td>
        <td>Easy</td>
        <td>Known plaintext attack on multi-byte XOR cipher</td>
      </tr>
      <tr>
        <td>CrackMe-01</td>
        <td>Crackmes.one</td>
        <td>Medium</td>
        <td>GDB dynamic analysis and anti-debugging bypass</td>
      </tr>
      <tr>
        <td>Obfuscator</td>
        <td>HackTheBox</td>
        <td>Hard</td>
        <td>Deobfuscating highly packed binary in IDA Pro</td>
      </tr>
    </tbody>
  </table>
</div>
