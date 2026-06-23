# Week 2 Summary — Technical Depth

> Days 7–12 | 2026-06-15 — 2026-06-20

---

## Week at a Glance
This week focused on hands-on offensive and defensive tooling: web application interception and automation with Burp Suite (Day 7), deep packet and passive reconnaissance with Wireshark/tshark (Day 8), social‑engineering and phishing workflows with Zphisher/SET (Day 9), DoS/DDoS experimentation and mitigation (Day 10), exploitation and payload workflows with Metasploit (Day 11), and online authentication brute-force tools including Hydra, Medusa, Ncrack, and Patator (Day 12).

---

## Top 3 Learnings

1. **Lab hygiene & OPSEC matter:** Always isolate vulnerable targets (host-only VMs) and avoid exposing test assets to the internet; misconfigured labs can be compromised quickly.
2. **Passive vs active discovery:** Wireshark/tshark provide forensic, context-rich visibility (passive), while tools like Nmap and Burp Intruder actively probe targets — both approaches complement each other for a full assessment.
3. **Tool selection and detection tradeoffs:** Automated brute-force (Hydra/Medusa/Ncrack) and Intruder-style attacks are powerful but require careful success/failure modeling and throttling to avoid lockouts and detection; defenses (rate limiting, SYN cookies, MFA) are effective when properly configured.

---

## Tools Used This Week
| Tool | Days Used | Comfort Level (1-5) |
|---|---:|---:|
| Burp Suite (Proxy, Repeater, Intruder) | Day 07 | 4 |
| Wireshark / tshark | Day 08 | 4 |
| Zphisher / SET / Ngrok | Day 09 | 3 |
| hping3 / Slowloris / iptables / sysctl | Day 10 | 3 |
| Metasploit (msfconsole, msfvenom) | Day 11 | 4 |
| Hydra / Medusa / Ncrack / Patator | Day 12 | 3 |

---

## Biggest Challenge
Modeling real-world constraints: simulating realistic attack delivery and detection (phishing asset fidelity, service rate limits, and callback network interfaces) required extra steps to avoid false negatives and self-inflicted lab outages. Solutions included scoped proxy rules, local tunneling for delivery tests, careful interface selection for payload callbacks, and conservative throttling during brute-force experiments.

---

## Skill Progression
| Skill Area | Start of Week | End of Week |
|---|---|---|
| Web testing | Basic proxy usage | Interception → automated brute-force (Intruder) |
| Packet analysis | Intro filters | Passive reconnaissance & extraction of credentials |
| Social engineering | Conceptual awareness | Built and hosted credential harvesters end-to-end |
| Network attacks | Conceptual DoS | Local transport & application-layer tests + mitigations |
| Exploitation | Familiarity with msfvenom | Full msfconsole workflow and Meterpreter basics |
| Authentication testing | Limited exposure | Multi-tool comparison (Hydra/Medusa/Ncrack/Patator) |

---

## Connections to Week 1
Foundational skills from Week 1 (Linux, basic networking, Nmap, and hashing) were reused and deepened: Nmap scan results fed Metasploit and Hydra workflows; Linux user/group and process knowledge helped when running tools and managing permissions; hashing/password-cracking concepts helped frame brute-force and credential-stuffing exercises.

---

## Looking Ahead to Week 3
Shift from tool-centric exercises to pattern recognition and detection: analyze logs and packet captures for brute-force and phishing indicators, build simple detection rules (Suricata/tshark filters), and practice pivoting from a compromised host to internal reconnaissance and lateral movement.

---

## Day-by-Day Links
- Day 07 — [Web Application Interception with Burp Suite](../daily-logs/week-02/day-07_2026-06-15.md)
- Day 08 — [Deep Packet Analysis with Wireshark](../daily-logs/week-02/day-08_2026-06-16.md)
- Day 09 — [Phishing and Credential Harvesting](../daily-logs/week-02/day-09_2026-06-17.md)
- Day 10 — [DoS & DDoS Experiments](../daily-logs/week-02/day-10_2026-06-18.md)
- Day 11 — [Metasploit Framework Workflows](../daily-logs/week-02/day-11_2026-06-19.md)
- Day 12 — [Hydra and Authentication Brute Force](../daily-logs/week-02/day-12_2026-06-20.md)

---

*Week 2 | Technical Depth — practical offensive and defensive tooling, 2026-06-15 → 2026-06-20*
