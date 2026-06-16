# Week 1 Summary — Foundation Week

> *Days 1–6 | 08-06-2026 (Monday) to 13-06-2026 (Saturday)*

---

## Week at a Glance

Week 1 was designed to build the foundational skills that every subsequent week depends on: Linux system administration, TCP/IP networking, network reconnaissance, identity management, and cryptographic hashing. The six days followed a deliberate progression — starting with the command line and filesystem (Days 1–2), moving into active network scanning and packet-level analysis (Day 3), then Linux user and group management with bash automation (Day 4), and culminating in cryptographic hashing theory with Hashcat (Day 5) and custom Python-based hash cracking automation (Day 6). By the end of the week, the gap between "knowing what a tool does" and "understanding why it works that way" became the central theme — a mindset shift from passive tool usage to active comprehension.

---

## Daily Breakdown

| Day | Date | Domain | Title | Key Deliverable |
|---|---|---|---|---|
| Day 01 | 08-06-2026 (Mon) | Linux / Networking | [Linux CLI & TCP/IP Basics](../daily-logs/week-01/day-01_2026-06-08.md) | Filesystem navigation, permissions model, TCP/IP four-layer model, IP classification |
| Day 02 | 09-06-2026 (Tue) | Linux Administration | [Filesystem Hierarchy & Directory Structure](../daily-logs/week-01/day-02_2026-06-09.md) | Complete FHS mapping — purpose and security implications of every top-level directory |
| Day 03 | 10-06-2026 (Wed) | Network Security | [Nmap Scanning & Wireshark Analysis](../daily-logs/week-01/day-03_2026-06-10.md) | SYN, Connect, UDP, ACK, Xmas scan types verified at packet level; NSE scripting |
| Day 04 | 11-06-2026 (Thu) | Linux Administration | [User/Group Management & Bash Automation](../daily-logs/week-01/day-04_2026-06-11.md) | Identity provisioning script deployed to `/usr/local/bin` as a system command |
| Day 05 | 12-06-2026 (Fri) | Cryptography | [Hashing & Password Cracking with Hashcat](../daily-logs/week-01/day-05_2026-06-12.md) | Mask, dictionary, and combinator attacks; hash identification workflow |
| Day 06 | 13-06-2026 (Sat) | Cryptography / Python | [Hash Cracking Automation with Python](../daily-logs/week-01/day-06_2026-06-13.md) | Custom SHA-512 brute-force script using `hashlib`; performance analysis |

---

## Top 5 Learnings

1. **The Linux filesystem is a security architecture, not just organization.**
   The separation of `/etc` (configuration), `/bin` (executables), and `/home` (user data) is a deliberate permission boundary. Virtual filesystems like `/proc` and `/sys` expose real-time kernel and process data — they are live intelligence sources during security assessments, not just system internals.

2. **Nmap scan types produce fundamentally different packet signatures.**
   Running Wireshark alongside Nmap made the theory concrete: SYN scans send SYN → receive SYN-ACK → immediately RST (half-open). Connect scans complete the full handshake. UDP scans rely on ICMP Port Unreachable for closed ports. Understanding *why* SYN scans need root (raw socket access for crafting custom TCP packets) is more important than memorizing the `-sS` flag.

3. **Hashing is one-way — cracking is about guessing, not reversing.**
   Whether using Hashcat's GPU-accelerated mask attacks or a custom Python `hashlib` script, the fundamental logic is identical: generate a candidate → hash it → compare. The algorithm's strength is irrelevant if the input is weak — a 7-digit numeric PIN falls in seconds regardless of whether it was hashed with MD5 or SHA-512.

4. **I/O is the bottleneck, not computation.**
   The Day 6 Python script ran 10x slower when printing every attempt to the terminal. This was the first practical encounter with the principle that I/O operations inside tight loops destroy performance — the same reason production tools like Hashcat run silently and report only results.

5. **Linux identity is purely numerical.**
   The system does not care about usernames — it operates on UIDs and GIDs. Any account with UID 0 is root, regardless of its name. Service accounts should never have home directories or valid login shells. The `-aG` flag in `usermod` is critical — forgetting the `-a` (append) strips all existing secondary groups, potentially breaking sudo access.

---

## Tools Inventory

| # | Tool | Category | Days Used | Comfort Level (1–5) | Key Insight |
|---|---|---|---|---|---|
| 1 | Bash | Shell / Scripting | Day 01–06 | 4 | Foundation of all system interaction; `sudo !!` for privilege recovery |
| 2 | ip (iproute2) | Network Analysis | Day 01 | 3 | Modern replacement for deprecated `ifconfig`; richer output for scripting |
| 3 | ss (iproute2) | Network Analysis | Day 01 | 3 | `ss -tuln` reveals every listening service — critical for security auditing |
| 4 | ping (iputils) | Network Analysis | Day 01 | 4 | Basic reachability; limited by ICMP filtering on hardened targets |
| 5 | curl | Network Analysis | Day 01 | 3 | HTTP header inspection with `-I`; protocol-level debugging |
| 6 | tree | Linux / System | Day 02 | 4 | `-L` depth limiting prevents overwhelming output; `--dirsfirst` for clarity |
| 7 | file / stat / find / cat | Linux / System | Day 02 | 4 | Content-based type identification, metadata inspection, filesystem search |
| 8 | Nmap | Network Security | Day 03 | 3 | Scan type selection requires understanding of TCP mechanics, not just flags |
| 9 | Wireshark | Network Security | Day 03 | 2 | Packet-level verification of scan behavior; will revisit in depth in Week 2 |
| 10 | useradd / userdel / usermod | Linux / System | Day 04 | 3 | `-aG` append trap; `-M` for service accounts; `-r` for clean deletion |
| 11 | groupadd / groupdel | Linux / System | Day 04 | 3 | Group-based permission management for multi-user environments |
| 12 | head / tail | Linux / System | Day 04 | 4 | Targeted file inspection without overwhelming terminal output |
| 13 | md5sum | Cryptography | Day 05 | 4 | `echo -n` is mandatory — trailing newline produces a completely different hash |
| 14 | hashid / hash-identifier | Cryptography | Day 05 | 3 | Cross-reference results with Hashcat example hashes when tools disagree |
| 15 | Hashcat | Cryptography | Day 05 | 3 | Potfile caching can cause "Exhausted" confusion; `--show` to check |
| 16 | Python (hashlib) | Cryptography / Scripting | Day 06 | 3 | `.encode('utf-8')` is mandatory; `getattr()` for dynamic algorithm selection |

---

## Concepts Learned

| # | Concept | Domain | Day |
|---|---|---|---|
| 1 | TCP/IP Model (4 layers) | Network Security | Day 01 |
| 2 | IPv4 Addressing & Classification | Network Security | Day 01 |
| 3 | TCP vs UDP (handshake vs connectionless) | Network Security | Day 01 |
| 4 | Private IP Ranges (RFC 1918) | Network Security | Day 01 |
| 5 | NAT (Network Address Translation) | Network Security | Day 01 |
| 6 | Linux File Permissions (octal notation) | Linux / OS | Day 01 |
| 7 | Filesystem Hierarchy Standard (FHS) | Linux / OS | Day 02 |
| 8 | Virtual Filesystems (`/proc`, `/sys`, `/dev`) | Linux / OS | Day 02 |
| 9 | Sticky Bit (`/tmp` protection) | Linux / OS | Day 02 |
| 10 | SYN, Connect, UDP, ACK, Xmas Scan Types | Network Security | Day 03 |
| 11 | Nmap Scripting Engine (NSE) | Network Security | Day 03 |
| 12 | UID/GID Identity Model | Linux / OS | Day 04 |
| 13 | Bash History Expansion (`!!`) | Linux / OS | Day 04 |
| 14 | Cryptographic Hashing (one-way functions) | Cryptography | Day 05 |
| 15 | Collision Resistance | Cryptography | Day 05 |
| 16 | Mask, Dictionary, and Combinator Attacks | Cryptography | Day 05 |
| 17 | Python hashlib Module | Cryptography | Day 06 |
| 18 | Brute-Force Attack Logic | Cryptography | Day 06 |

**Total: 18 concepts across 3 domains in 6 days.**

---

## Challenges and Resolutions

| Day | Challenge | Root Cause | Resolution | Key Realization |
|---|---|---|---|---|
| Day 01 | `ifconfig` returned "command not found" | Arch Linux ships `iproute2`, not deprecated `net-tools` | Used `ip addr show` and `ss` as modern equivalents | Tools evolve — modern replacements provide richer output |
| Day 02 | `tree /` produced overwhelming, infinite output | Recursive traversal of virtual filesystems `/proc`, `/sys` | Scoped with `tree -L 1 /` and `tree -L 2 /etc` | Always scope tools to the exact depth needed |
| Day 03 | `nmap -sS` silently fell back to TCP Connect scan | SYN scan requires raw sockets → needs root or `CAP_NET_RAW` | Ran with `sudo`; verified half-open behavior in Wireshark | Understanding the privilege model is as critical as knowing the syntax |
| Day 04 | New user had a featureless `$` prompt without tab completion | `useradd` defaulted to `/bin/sh` (dash) instead of `/bin/bash` | Fixed with `usermod -s /bin/bash`; always specify shell explicitly | Never assume defaults — explicit configuration prevents silent failures |
| Day 05 | Hashcat exited with "Exhausted" despite correct wordlist | Hash was already cracked and cached in the potfile | Used `--show` to retrieve cached result; `--potfile-disable` to re-crack | Tools cache aggressively for efficiency — know where state is stored |
| Day 06 | Script ran 10x slower than expected (minutes instead of seconds) | `print()` on every iteration created terminal I/O bottleneck | Removed per-iteration output; print only on match/exhaustion | I/O inside tight loops is a performance anti-pattern in security tooling |

---

## Biggest Challenge

**Day 03 — Nmap privilege escalation and silent fallback.**

Running `nmap -sS 192.0.2.1` without `sudo` did not produce an error — it silently downgraded to a TCP Connect scan (`-sT`). This was the most dangerous type of failure: a tool appearing to work correctly while producing fundamentally different behavior. The SYN scan was intended to be "stealthy" (no full handshake), but the fallback to Connect scan completed full TCP handshakes on every port, generating significantly more noise and log entries on the target.

The fix was simple (`sudo`), but the lesson was deeper: **silent fallbacks are more dangerous than loud errors.** An error message forces investigation; a silent behavioral change can go unnoticed and lead to incorrect conclusions. Verifying the actual packet behavior in Wireshark — rather than trusting the tool's output alone — became a permanent habit after this incident.

---

## Skill Progression

| Skill Area | Start of Week | End of Week | Evidence |
|---|---|---|---|
| Linux CLI & Administration | Beginner | Comfortable | Navigate filesystem, manage permissions, inspect processes, manage users/groups |
| TCP/IP Networking | Beginner | Intermediate | Understand all 4 layers, IP classification, TCP vs UDP mechanics, NAT |
| Network Scanning (Nmap) | No experience | Intermediate | Execute 6+ scan types, understand packet-level differences, use NSE scripts |
| Packet Analysis (Wireshark) | No experience | Foundational | Capture traffic, apply basic display filters, verify scan behavior |
| Cryptography & Hashing | No experience | Intermediate | Generate, identify, and crack hashes; understand algorithm strengths and weaknesses |
| Bash Scripting | Beginner | Basic Automation | Wrote and deployed a system-level provisioning script |
| Python Scripting | Beginner | Basic Automation | Wrote a functional hash cracker with timing and dynamic algorithm support |

---

## Patterns and Emerging Themes

Three recurring patterns emerged across the week that will likely define the internship's learning trajectory:

1. **The "why" matters more than the "how."** Every tool has a `--help` page. The real value is understanding the underlying mechanism — why SYN scans need root, why hashing is one-way, why `/etc/shadow` has `600` permissions. Surface-level tool usage is fragile; understanding the principle behind it is transferable.

2. **Verification is non-negotiable.** Day 3 (Wireshark verifying Nmap behavior), Day 4 (checking `/etc/passwd` after `useradd`), Day 5 (cross-referencing `hashid` results against Hashcat example hashes) — every day reinforced the habit of independently verifying tool output rather than assuming correctness.

3. **Security is about constraints, not features.** File permissions, the sticky bit, service account restrictions (`-M`, no shell), and the principle of least privilege are all about *removing* access, not adding capabilities. The security mindset is fundamentally about asking "what should NOT be allowed?" rather than "what should work?"

---

## Looking Ahead to Week 2

Week 2 ("Technical Depth") will transition from foundational tool usage to applied security workflows:

- **Web application security** — Setting up Burp Suite as an intercepting proxy, deploying Metasploitable 2 as a deliberately vulnerable target, and exploring interception, modification, and automated attacks against web applications
- **Advanced packet analysis** — Returning to Wireshark with a focus on deep display/capture filters, cleartext credential extraction, service fingerprinting, and network anomaly detection
- **Tool integration** — Combining skills across domains (e.g., using Nmap to discover services, Wireshark to analyze their traffic, and Burp Suite to test their web interfaces)

---

*Week 1 | Foundation Week | Linux Administration, Networking, Cryptography*
*Total: 6 daily logs · 16 tools · 18 concepts · 6 challenges resolved*
