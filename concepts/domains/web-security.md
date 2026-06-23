# Web Application Security

Concepts for testing and securing web applications, including HTTP interception, fuzzing, and injection attacks.

## HTTP Interception & Proxying

Tools and techniques for inspecting and modifying web traffic.

- [[concepts-glossary#Intercepting Proxy]] — Tools like Burp Suite that capture HTTP/HTTPS traffic
- Allows modification of requests/responses before delivery

## Burp Suite Modules

Manual and automated web security testing capabilities.

- [[concepts-glossary#Burp Repeater]] — Manual request modification and resending
- [[concepts-glossary#Burp Intruder]] — Automated payload fuzzing with multiple attack modes
- [[concepts-glossary#Intruder Attack Types (Sniper, Battering Ram, Pitchfork, Cluster Bomb)]] — Payload iteration strategies

## Testing Techniques

Methodologies for discovering vulnerabilities.

- [[concepts-glossary#Response Size Analysis]] — Identifying successful payloads by comparing HTTP response lengths
- Useful for brute-forcing authentication and finding information disclosure

## Information Disclosure

How servers leak sensitive information.

- [[concepts-glossary#HTTP Header Information Leakage]] — Server version, language runtime, OS exposed via headers
- Reduces attacker reconnaissance effort

## Vulnerable Application Testing

Safe environments for practicing attacks.

- [[concepts-glossary#Deliberately Vulnerable Application]] — DVWA, Metasploitable 2, intentionally insecure for labs

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

- [[network-security]] — HTTP and protocol fundamentals
- [[cryptography]] — HTTPS and TLS
- [[social-engineering]] — Credential harvesting through web interfaces
- [[offensive-security]] — Exploitation and post-exploitation
- [[concepts/INDEX]] — All domains
