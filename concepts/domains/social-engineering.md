# Social Engineering

Techniques for manipulating human psychology to compromise security through non-technical means.

## Phishing & Impersonation

Email-based and website-based attacks targeting credentials.

- [[concepts-glossary#Phishing]] — Impersonating trusted entities to steal credentials
- [[concepts-glossary#Spear Phishing]] — Targeted phishing using OSINT for personalization
- [[concepts-glossary#Clone Phishing]] — Duplicating legitimate emails with malicious links

## Credential Harvesting

Techniques for capturing usernames and passwords.

- [[concepts-glossary#Credential Harvesting]] — Serving fake login pages to capture credentials
- Related tools: [[#zphisher]], [[#SET (Social Engineering Toolkit)]]

## Attack Lifecycle

Full structure of social engineering campaigns.

- [[concepts-glossary#Social Engineering Kill Chain]] — Reconnaissance → Weaponization → Delivery → Exploitation → Post-Exploitation → Covering Tracks

## Defense: Authentication

Phishing-resistant security measures.

- [[concepts-glossary#Phishing-Resistant Authentication (FIDO2/WebAuthn)]] — Cryptographic keys bound to legitimate domains only
- [[concepts-glossary#DMARC (Domain-based Message Authentication)]] — Email authentication protocol combining SPF and DKIM

## Related Networking

Tools for delivery and command & control.

- [[#Ngrok]] — Secure tunneling to expose local servers publicly
- Used in credential harvesting and C2 communication

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 09 | Phishing, Spear Phishing, Credential Harvesting, Clone Phishing, Social Engineering Kill Chain, DMARC, Phishing-Resistant Authentication |

---

## See Also

- [[web-security]] — Website cloning and Burp Intruder
- [[network-security]] — Protocol security and encryption
- [[offensive-security]] — Post-exploitation after credential theft
- [[concepts/INDEX]] — All domains
