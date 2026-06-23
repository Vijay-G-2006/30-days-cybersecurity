# Web Application Security

Concepts for testing and securing web applications, including HTTP interception, fuzzing, and injection attacks.

## HTTP Interception & Proxying

Tools and techniques for inspecting and modifying web traffic.

- [Intercepting Proxy](../concepts-glossary.md#intercepting-proxy) — Tools like Burp Suite that capture HTTP/HTTPS traffic
- Allows modification of requests/responses before delivery

## Burp Suite Modules

Manual and automated web security testing capabilities.

- [Burp Repeater](../concepts-glossary.md#burp-repeater) — Manual request modification and resending
- [Burp Intruder](../concepts-glossary.md#burp-intruder) — Automated payload fuzzing with multiple attack modes
- [Intruder Attack Types (Sniper, Battering Ram, Pitchfork, Cluster Bomb)](../concepts-glossary.md#intruder-attack-types-sniper-battering-ram-pitchfork-cluster-bomb) — Payload iteration strategies

## Testing Techniques

Methodologies for discovering vulnerabilities.

- [Response Size Analysis](../concepts-glossary.md#response-size-analysis) — Identifying successful payloads by comparing HTTP response lengths
- Useful for brute-forcing authentication and finding information disclosure

## Information Disclosure

How servers leak sensitive information.

- [HTTP Header Information Leakage](../concepts-glossary.md#http-header-information-leakage) — Server version, language runtime, OS exposed via headers
- Reduces attacker reconnaissance effort

## Vulnerable Application Testing

Safe environments for practicing attacks.

- [Deliberately Vulnerable Application](../concepts-glossary.md#deliberately-vulnerable-application) — DVWA, Metasploitable 2, intentionally insecure for labs

## SQL Injection

Database-level attacks through HTTP parameters.

- SQL Injection concepts (from Day 14)
- Related tool: [[#sqlmap]] for automated detection and exploitation

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 07 | Intercepting Proxy, Burp Repeater, Burp Intruder, Intruder Attack Types, Response Size Analysis, HTTP Header Leakage, Deliberately Vulnerable Application |
| Day 14 | SQL Injection |

---

## See Also

- [Network Security](network-security.md) — HTTP and protocol fundamentals
- [Cryptography](cryptography.md) — HTTPS and TLS
- [Social Engineering](social-engineering.md) — Credential harvesting through web interfaces
- [Offensive Security](offensive-security.md) — Exploitation and post-exploitation
- [All domains](../INDEX.md) — All domains
