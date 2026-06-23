# Cryptography & Password Security

Concepts related to hashing, encryption, password recovery, and cryptographic fundamentals.

## Hashing Fundamentals

One-way functions used for password storage and integrity verification.

- [[concepts-glossary#Cryptographic Hashing]] — Deterministic one-way function producing fixed-size output
- [[concepts-glossary#Collision Resistance]] — Computational infeasibility of finding hash collisions

## Password Cracking Techniques

Methods for recovering passwords from hashes.

- [[concepts-glossary#Brute-Force Attack (Hashing)]] — Testing every possible input against target hash
- [[concepts-glossary#Dictionary Attack (Hashcat -a 0)]] — Testing wordlist entries (rockyou.txt, etc.)
- [[concepts-glossary#Combinator Attack (Hashcat -a 1)]] — Combining words from multiple dictionaries
- [[concepts-glossary#Mask Attack (Hashcat -a 3)]] — Pattern-based guessing (lowercase + 4 digits)

## Tools & Implementation

Practical tools for hashing and password recovery.

- [[concepts-glossary#Python hashlib]] — Built-in module for generating hashes
- Hashcat for GPU-accelerated password cracking
- Hashid / Hash-identifier for identifying hash types

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 05 | Cryptographic Hashing, Collision Resistance, Mask Attack, Dictionary Attack, Combinator Attack |
| Day 06 | Python hashlib, Brute-Force Attack (Hashing) |

---

## See Also

- [[web-security]] — HTTPS and TLS
- [[network-security]] — Encrypted vs. unencrypted protocols
- [[linux-systems]] — Password files and shadow hashing
- [[offensive-security]] — Post-exploitation credential harvesting
- [[concepts/INDEX]] — All domains
