# Social Engineering

Techniques for manipulating human psychology to compromise security through non-technical means.

## Phishing & Impersonation

Email-based and website-based attacks targeting credentials.

- [Phishing](../concepts-glossary.md#phishing) — Impersonating trusted entities to steal credentials
- [Spear Phishing](../concepts-glossary.md#spear-phishing) — Targeted phishing using OSINT for personalization
- [Clone Phishing](../concepts-glossary.md#clone-phishing) — Duplicating legitimate emails with malicious links

## Credential Harvesting

Techniques for capturing usernames and passwords.

- [Credential Harvesting](../concepts-glossary.md#credential-harvesting) — Serving fake login pages to capture credentials
- Related tools: [Zphisher](#zphisher), [SET (Social Engineering Toolkit)](#set-social-engineering-toolkit)

## Attack Lifecycle

Full structure of social engineering campaigns.

- [Social Engineering Kill Chain](../concepts-glossary.md#social-engineering-kill-chain) — Reconnaissance → Weaponization → Delivery → Exploitation → Post-Exploitation → Covering Tracks

## Defense: Authentication

Phishing-resistant security measures.

- [Phishing-Resistant Authentication (FIDO2/WebAuthn)](../concepts-glossary.md#phishing-resistant-authentication-fido2webauthn) — Cryptographic keys bound to legitimate domains only
- [DMARC (Domain-based Message Authentication)](../concepts-glossary.md#dmarc-domain-based-message-authentication) — Email authentication protocol combining SPF and DKIM

## Related Networking

Tools for delivery and command & control.

- [Ngrok](#ngrok) — Secure tunneling to expose local servers publicly
- Used in credential harvesting and C2 communication

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 09 | Phishing, Spear Phishing, Credential Harvesting, Clone Phishing, Social Engineering Kill Chain, DMARC, Phishing-Resistant Authentication |

---

## See Also

- [Web Security](web-security.md) — Website cloning and Burp Intruder
- [Network Security](network-security.md) — Protocol security and encryption
- [Offensive Security](offensive-security.md) — Post-exploitation after credential theft
- [All domains](../INDEX.md) — All domains
