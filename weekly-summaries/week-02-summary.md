# Week 2 Summary — Technical Depth

> Days 7–12 | 2026-06-15 — 2026-06-20

---

## Week at a Glance

Week 2 dove into practical offensive and defensive workflows across web application security, packet-level analysis, social engineering, denial-of-service experimentation, exploit development via Metasploit, and online authentication testing. The week emphasized a pipeline approach: discover (Nmap/tshark), intercept and modify (Burp Suite), automate attacks (Intruder / Hydra / Medusa / Patator), and validate detection and mitigation (iptables, sysctl, response-size analysis). Hands-on labs used an isolated Metasploitable 2 VM and host-only networking for safe experimentation.

---

## Daily Breakdown

| Day | Date | Domain | Title | Key Deliverable |
|---|---|---|---|---|
| Day 07 | 2026-06-15 | Web Application Security | [Burp Suite: Proxy, Repeater, Intruder](../daily-logs/week-02/day-07_2026-06-15.md) | Lab setup with Metasploitable 2, scoped proxy rules, automated login brute-force with Intruder and success detection via response length |
| Day 08 | 2026-06-16 | Network Security | [Wireshark & tshark Deep Analysis](../daily-logs/week-02/day-08_2026-06-16.md) | Non-root capture setup, advanced display/capture filters, passive service/version extraction and credential recovery from cleartext protocols |
| Day 09 | 2026-06-17 | Social Engineering | [Phishing & Credential Harvesting](../daily-logs/week-02/day-09_2026-06-17.md) | Built phishing pages with Zphisher and SET; tested local and tunneled delivery (Ngrok); compared fidelity and reporting between tools |
| Day 10 | 2026-06-18 | Network Security | [DoS / DDoS Experiments](../daily-logs/week-02/day-10_2026-06-18.md) | Local SYN/UDP floods with `hping3` and application-layer exhaustion with Slowloris; measured socket state and validated kernel mitigations (SYN cookies, iptables rate limiting) |
| Day 11 | 2026-06-19 | Offensive Security | [Metasploit Framework](../daily-logs/week-02/day-11_2026-06-19.md) | `msfconsole` workflow, `db_nmap` integration, payload creation with `msfvenom`, Meterpreter session basics and post-exploitation modules |
| Day 12 | 2026-06-20 | Authentication Testing | [Hydra & Brute-Force Tools](../daily-logs/week-02/day-12_2026-06-20.md) | Online brute-force testing with Hydra, Medusa, Ncrack, and Patator; HTTP form modeling and failure-pattern detection |

---

## Top 5 Learnings

1. **Scoped labs and OPSEC are mandatory.** Running deliberate vulnerability labs (Metasploitable 2) without proper isolation risks uncontrolled compromise; host-only networks, scoped proxy rules, and careful tunneling choices (Ngrok with auth tokens) were essential safeguards.
2. **Response-size analysis is a pragmatic signal.** For web-based brute-force and Intruder-style attacks, raw HTTP status codes are often ambiguous — sorting by response `Content-Length` or looking for redirect behavior reliably surfaced successful authentication attempts.
3. **Passive analysis complements active scanning.** `tshark`/Wireshark provided contextual evidence (actual protocol exchanges, banners, cleartext credentials) that enriched Nmap and Metasploit findings and helped tune automated attacks to avoid false negatives.
4. **Customization and throttling reduce noise and lockouts.** Tools like Patator and Medusa provide finer control over concurrency and success-matching; aggressive defaults (Hydra `--fork` or `--t` values) triggered service protections in the lab and required conservative tuning.
5. **Defensive controls are immediately effective.** Enabling `tcp_syncookies`, tuning `tcp_max_syn_backlog`, and applying `iptables` rate limits materially preserved service availability during simulated floods — demonstrating practical, deployable mitigations.

---

## Tools Used This Week
| # | Tool | Days Used | Comfort Level (1–5) | Key Role |
|---|---|---:|---:|---|
| 1 | Burp Suite (Proxy / Repeater / Intruder) | Day 07 | 4 | Intercept, modify, and automate web requests; Intruder payload workflows |
| 2 | Wireshark / tshark | Day 08 | 4 | Deep packet inspection, passive fingerprinting, credential extraction |
| 3 | Zphisher / SET / Ngrok | Day 09 | 3 | Rapid phishing page creation and external delivery testing |
| 4 | hping3 / Slowloris | Day 10 | 3 | Transport- and application-layer DoS simulations |
| 5 | iptables / sysctl | Day 10 | 3 | Kernel and firewall mitigations (rate limiting, SYN cookies) |
| 6 | Metasploit (msfconsole / msfvenom) | Day 11 | 4 | Modular exploitation, workspace/db integration, Meterpreter sessions |
| 7 | Hydra / Medusa / Ncrack / Patator | Day 12 | 3 | Online authentication testing and comparative tool evaluation |
| 8 | Nmap | Days 07-12 | 4 | Service discovery and input to both Metasploit and brute-force workflows |

---

## Concepts Learned

| # | Concept | Domain | Day |
|---|---|---|---:|
| 1 | Proxy scoping & CA trusts | Web Security | Day 07 |
| 2 | Intruder attack types (Sniper, Pitchfork, Cluster Bomb) | Web Security | Day 07 |
| 3 | Capture vs display filters (BPF vs Wireshark) | Network Forensics | Day 08 |
| 4 | Passive service/version extraction | Network Forensics | Day 08 |
| 5 | Phishing kill chain & hosting options | Social Engineering | Day 09 |
| 6 | Asset fidelity for phishing pages (templates vs live clone) | Social Engineering | Day 09 |
| 7 | SYN flood vs application-layer DoS | Network Security | Day 10 |
| 8 | Kernel-level mitigations (`tcp_syncookies`) | Network Security | Day 10 |
| 9 | Metasploit module taxonomy (exploit/aux/post/payload) | Offensive Security | Day 11 |
| 10 | Meterpreter basics & LHOST/LPORT callback considerations | Offensive Security | Day 11 |
| 11 | Online brute-force strategies: spraying, stuffing, throttling | Authentication Testing | Day 12 |
| 12 | Failure-pattern matching for HTTP forms | Authentication Testing | Day 12 |

**Total: 12 concepts across 4 domains.**

---

## Challenges and Resolutions

| Day | Challenge | Root Cause | Resolution | Key Realization |
|---|---|---|---|---|
| Day 07 | Proxy intercepted too many assets, slowing tests | Default intercept caught CSS/JS/images | Scoped target in Burp and filtered static assets | Scoping makes interactive testing practical |
| Day 08 | No capture devices shown in GUI | User not in `wireshark` group / dumpcap caps missing | Added user to group, set `cap_net_raw` on `dumpcap` | Use capabilities instead of running GUI as root |
| Day 09 | Cloned pages missing external assets | Live clone referenced external CDNs and CSP blocks | Embedded critical assets locally or use template-based pages | Visual fidelity strongly affects phishing success |
| Day 10 | Self-inflicted DoS during `hping3` tests | Targeted localhost without limits; root required | Short bursts, monitor `ss`, enable `tcp_syncookies` and rate limiting | Always have an escape plan and monitoring when running floods |
| Day 11 | Exploit callbacks failed | Wrong `LHOST` on multi-homed host | Use host-only interface IP reachable by target; verify with `ip addr` | Correct callback interface is essential for success |
| Day 12 | HTTP brute-force returned false negatives | Incorrect failure string or response model | Inspect raw response, correct failure pattern, re-run | HTTP forms require precise modeling to detect success |

---

## Biggest Challenge

Balancing realism with safety: reproducing realistic delivery and detection conditions (pixel-perfect phishing pages, tunneled delivery, realistic userlists, correct callback interfaces) without exposing lab assets to the internet or accidentally taking down the host required careful orchestration. The practical solution was a set of operational controls: host-only networking, scoped proxy rules, conservative throttling, and validating every attack using passive forensics (tshark/Wireshark) before scaling.

---

## Skill Progression
| Skill Area | Start of Week | End of Week | Evidence |
|---|---|---|---|
| Web Application Testing | Basic proxy navigation | Interception → automated brute-force workflows | Burp Intruder attacks and response-size detection (Day 07) |
| Packet Analysis | Foundational filters | Passive fingerprinting and credential extraction | `tshark` scripts and Wireshark recon (Day 08) |
| Social Engineering | Conceptual | End-to-end phishing delivery and capture | Zphisher/SET runs and Ngrok-hosted tests (Day 09) |
| DoS Testing & Mitigation | Conceptual | Controlled local attacks with mitigations | `hping3`, Slowloris, `iptables`, `tcp_syncookies` (Day 10) |
| Exploitation | Reconnaissance only | Full msfconsole → Meterpreter workflow | `db_nmap` import, `msfvenom` payloads, Meterpreter (Day 11) |
| Authentication Testing | Awareness | Tool comparison and modeling | Hydra/Medusa/Ncrack/Patator experiments (Day 12) |

---

## Patterns and Emerging Themes

1. **Tool interoperability is powerful.** Nmap discoveries fed Metasploit and Hydra workflows; Wireshark confirmed what automated tools reported. Integrating discovery, attack, and forensic tools produced reproducible results.
2. **Modeling the target is often the hard part.** For HTTP attacks, modeling form fields and failure responses is as important as wordlists — naive automation yields noise, not results.
3. **Small, deliberate mitigations scale.** Simple kernel and firewall settings (SYN cookies, rate limiting) provided large resilience gains against local attacks — a strong argument for defense-in-depth.

---

## Looking Ahead to Week 3
Move from tool fluency to pattern recognition and detection: build simple detection rules (tshark filters, Suricata signatures) for brute-force and phishing indicators, practice log analysis for authentication anomalies, and begin safe pivoting and lateral movement exercises from a compromised host.

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
