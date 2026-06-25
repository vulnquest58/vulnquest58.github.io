---
layout: post
title: "Writeup Template"
date: 2026-01-15
category: bugbounty
tags: [template, writeup]
severity: critical
target: example.com
program: hackerone
status: disclosed
---

# Vulnerability Title

## Summary

Brief overview of the vulnerability and its impact.

**Severity**: Critical / High / Medium / Low  
**CVSS Score**: X.X  
**Reward**: $X,XXX  
**Program**: Program Name  

## Vulnerability Details

### Type
[e.g., SQL Injection, XSS, IDOR, SSRF, RCE]

### Affected Endpoint
```
https://target.com/vulnerable/endpoint
```

### Root Cause
Explanation of why the vulnerability exists.

## Steps to Reproduce

### Prerequisites
- Account with [role] privileges
- Access to [specific feature]

### Reproduction Steps

1. **Step 1**: Navigate to [URL]
   ```bash
   curl -X GET "https://target.com/endpoint"
   ```

2. **Step 2**: Perform action
   - Open browser developer tools
   - Intercept request with Burp Suite

3. **Step 3**: Inject payload
   ```
   Payload: [malicious_input]
   ```

4. **Step 4**: Observe result
   - Expected: [normal behavior]
   - Actual: [vulnerable behavior]

## Proof of Concept

### HTTP Request
```http
GET /vulnerable/endpoint?param=payload HTTP/1.1
Host: target.com
Cookie: session=abc123
```

### HTTP Response
```http
HTTP/1.1 200 OK
Content-Type: application/json

{
  "data": "sensitive_information"
}
```

### Screenshots

![PoC Screenshot](/assets/images/screenshots/poc-example.png)

### Video Demonstration

[Link to video demonstration]

## Impact

### What an Attacker Can Do
- Access sensitive data
- Escalate privileges
- Execute arbitrary code
- [Other impacts]

### Affected Data
- User credentials
- Personal information
- Financial data
- [Other data types]

### Business Impact
- Financial loss
- Reputation damage
- Regulatory compliance issues
- [Other impacts]

## Remediation

### Recommended Fix

```python
# Example secure code
import hashlib
import secrets

def secure_function(user_input):
    # Sanitize input
    sanitized = sanitize_input(user_input)
    
    # Use parameterized queries
    cursor.execute("SELECT * FROM users WHERE id = %s", (sanitized,))
    
    return result
```

### Security Controls

1. **Input Validation**
   - Whitelist allowed characters
   - Validate data types
   - Check length limits

2. **Output Encoding**
   - HTML encode for web context
   - URL encode for parameters
   - Use secure frameworks

3. **Access Controls**
   - Implement proper authentication
   - Enforce authorization checks
   - Use role-based access control

## Timeline

| Date | Event |
|------|-------|
| YYYY-MM-DD | Vulnerability discovered |
| YYYY-MM-DD | Report submitted |
| YYYY-MM-DD | Report triaged |
| YYYY-MM-DD | Fix deployed |
| YYYY-MM-DD | Bounty awarded |
| YYYY-MM-DD | Public disclosure |

## Lessons Learned

### What Went Well
- [Successful techniques]

### Challenges Faced
- [Obstacles encountered]

### Key Takeaways
- [Important lessons]

## References

- [OWASP Top 10](https://owasp.org/www-project-top-ten/)
- [CWE Entry](https://cwe.mitre.org/)
- [Related CVE](https://cve.mitre.org/)
- [Research Paper](url)
- [Blog Post](url)

## Acknowledgments

Thanks to [Program/Company] for their responsible disclosure program and quick response.

---

**Disclaimer**: This writeup is published after responsible disclosure and with permission. All sensitive information has been redacted.