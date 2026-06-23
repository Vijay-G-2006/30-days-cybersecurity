# Offensive Security

Exploitation frameworks, post-exploitation, privilege escalation, and active attack techniques.

## Metasploit Framework

Comprehensive penetration testing and exploitation platform.

- [Metasploit Framework](../concepts-glossary.md#metasploit-framework) — Modular framework with exploits, payloads, and auxiliary modules
- [msfconsole](#msfconsole) — Primary interactive console for running attacks
- [msfvenom](#msfvenom) — Payload generation and encoding tool

## Payload & Session Management

Executing code on compromised systems.

- [Meterpreter](../concepts-glossary.md#meterpreter) — Advanced interactive shell with file ops and post-exploitation capabilities
- Provides access for running post modules and lateral movement

## Metasploit Modules

Different types of modules for different attack phases.

- [Auxiliary Module](../concepts-glossary.md#auxiliary-module) — Scanning, enumeration, brute forcing (non-exploit)
- [Post Module](../concepts-glossary.md#post-module) — Credential harvesting, privilege escalation, pivoting after compromise

## Credential-Based Attacks

Post-exploitation techniques for gaining further access.

- [Brute-Force Attack (Authentication)](#brute-force-attack-authentication) — Trying username/password combinations
- Related tools: [Hydra](#hydra), [Medusa](#medusa), [Ncrack](#ncrack), [Patator](#patator)

## Exploitation Topics

- Vulnerable application targeting (DVWA, Metasploitable 2)
- SQL Injection via sqlmap
- Reverse shells and command execution

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 11 | Metasploit Framework, msfconsole, msfvenom, Meterpreter, Auxiliary Modules, Post Modules |
| Day 12 | Hydra, Medusa, Ncrack, Patator (brute-force tools) |
| Day 13-14 | SQL Injection, database enumeration |

---

## See Also

- [Linux Systems](linux-systems.md) — OS internals for privilege escalation
- [Cryptography](cryptography.md) — Credential harvesting and password cracking
- [Web Security](web-security.md) — Application-level exploitation
- [Social Engineering](social-engineering.md) — Initial access via phishing
- [Network Security](network-security.md) — Network reconnaissance and C2
- [All domains](../INDEX.md) — All domains
