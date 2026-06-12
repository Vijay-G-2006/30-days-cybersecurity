# ✅ Pre-Publish OPSEC Checklist

**Run through this checklist before every commit, LinkedIn post, or blog article.**

Write as if your manager and the client's CISO are both subscribed to your feed.

---

## The Checklist

- [ ] Does this post **name the company**, a client, or a partner?
- [ ] Does this post include any **real IP address**, hostname, or domain?
- [ ] Does any screenshot contain **internal branding**, real IPs, or internal paths?
- [ ] Does this reveal a **specific unpatched vulnerability** in a production system?
- [ ] Does this reveal **internal network topology**, architecture, or design choices?
- [ ] Would my **manager be uncomfortable** reading this post?
- [ ] Would a **malicious actor gain useful information** from this post?

> **If ANY answer is Yes → sanitize or remove before publishing.**

---

## Quick Sanitization Reference

### IP Addresses — Use IETF Documentation Ranges
| Replace with | Range |
|---|---|
| `192.0.2.x` | TEST-NET-1 |
| `198.51.100.x` | TEST-NET-2 |
| `203.0.113.x` | TEST-NET-3 |

### Hostnames — Use Generic Placeholders
- `webserver-01`, `db-primary`, `corp-dc`
- Never include `.internal`, `.local`, or company TLDs

### Organization — Use Neutral References
- `[My Internship Organization]`
- `my current internship`

### Screenshots — Triple-Check
1. Window titles & UI branding
2. IP addresses, hostnames, usernames in tool output
3. Internal paths (`C:\CompanyName\...`, `/opt/companyname/...`)
4. Blur or crop anything that fails

---

## The Golden Rule

> **Focus on the *generic technique*, not the *specific operational context.***
>
> ✅ "Analyzing TLS handshakes in Wireshark"
>
> ❌ "Analyzing traffic between our customer portal and the payment gateway"

---

*📌 Laminate this in your brain. One careless post can end an internship.*
