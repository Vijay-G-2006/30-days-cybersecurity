# Cryptography & Password Security

Concepts related to hashing, encryption, password recovery, and cryptographic fundamentals.

## Hashing Fundamentals

One-way functions used for password storage and integrity verification.

- [Cryptographic Hashing](../concepts-glossary.md#cryptographic-hashing) — Deterministic one-way function producing fixed-size output
- [Collision Resistance](../concepts-glossary.md#collision-resistance) — Computational infeasibility of finding hash collisions

## Password Cracking Techniques

Methods for recovering passwords from hashes.

- [Brute-Force Attack (Hashing)](../concepts-glossary.md#brute-force-attack-hashing) — Testing every possible input against target hash
- [Dictionary Attack (Hashcat -a 0)](../concepts-glossary.md#dictionary-attack-hashcat--a-0) — Testing wordlist entries (rockyou.txt, etc.)
- [Combinator Attack (Hashcat -a 1)](../concepts-glossary.md#combinator-attack-hashcat--a-1) — Combining words from multiple dictionaries
- [Mask Attack (Hashcat -a 3)](../concepts-glossary.md#mask-attack-hashcat--a-3) — Pattern-based guessing (lowercase + 4 digits)

## Tools & Implementation

Practical tools for hashing and password recovery.

- [Python hashlib](../concepts-glossary.md#python-hashlib) — Built-in module for generating hashes
- Hashcat for GPU-accelerated password cracking
- Hashid / Hash-identifier for identifying hash types

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 05 | Cryptographic Hashing, Collision Resistance, Mask Attack, Dictionary Attack, Combinator Attack |
| Day 06 | Python hashlib, Brute-Force Attack (Hashing) |

---

## See Also

- [Web Security](web-security.md) — HTTPS and TLS
- [Network Security](network-security.md) — Encrypted vs. unencrypted protocols
- [Linux Systems](linux-systems.md) — Password files and shadow hashing
- [Offensive Security](offensive-security.md) — Post-exploitation credential harvesting
- [All domains](../INDEX.md) — All domains
