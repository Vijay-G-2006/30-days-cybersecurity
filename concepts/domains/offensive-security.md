# Offensive Security

Exploitation frameworks, post-exploitation, privilege escalation, and active attack techniques.

## Metasploit Framework

Comprehensive penetration testing and exploitation platform.

- [[concepts-glossary#Metasploit Framework]] — Modular framework with exploits, payloads, and auxiliary modules
- [[concepts-glossary#msfconsole]] — Primary interactive console for running attacks
- [[concepts-glossary#msfvenom]] — Payload generation and encoding tool

## Payload & Session Management

Executing code on compromised systems.

- [[concepts-glossary#Meterpreter]] — Advanced interactive shell with file ops and post-exploitation capabilities
- Provides access for running post modules and lateral movement

## Metasploit Modules

Different types of modules for different attack phases.

- [[concepts-glossary#Auxiliary Module]] — Scanning, enumeration, brute forcing (non-exploit)
- [[concepts-glossary#Post Module]] — Credential harvesting, privilege escalation, pivoting after compromise

## Credential-Based Attacks

Post-exploitation techniques for gaining further access.

- [[concepts-glossary#Brute-Force Attack (Authentication)]] — Trying username/password combinations
- Related tools: [[#Hydra]], [[#Medusa]], [[#Ncrack]], [[#Patator]]

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

- [[linux-systems]] — OS internals for privilege escalation
- [[cryptography]] — Credential harvesting and password cracking
- [[web-security]] — Application-level exploitation
- [[social-engineering]] — Initial access via phishing
- [[network-security]] — Network reconnaissance and C2
- [[concepts/INDEX]] — All domains
