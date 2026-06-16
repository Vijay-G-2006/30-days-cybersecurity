# Week 1 Summary — Foundation Week

> *Days 1–6 | 08-06-2026 to 13-06-2026*

---

## Week at a Glance
Week 1 established the foundational pillars of the internship: Linux system administration, TCP/IP networking, network scanning, and cryptography. The trajectory moved from navigating the filesystem and understanding permissions (Days 1–2), through active network reconnaissance with Nmap and Wireshark (Day 3), into Linux identity management and bash automation (Day 4), and culminated with cryptographic hashing theory, Hashcat-based password cracking (Day 5), and Python-based hash brute-forcing automation (Day 6).

---

## Top 3 Learnings

1. **The Linux filesystem is a security architecture, not just an organizational convention:** The separation of `/etc` (configuration), `/bin` (executables), and `/home` (user data) enables granular access control. Virtual filesystems like `/proc` expose real-time process data that is invaluable during security assessments.
2. **Nmap scan types produce fundamentally different packet behaviors:** Running Wireshark alongside Nmap made the difference between SYN scans (half-open), TCP Connect scans (full handshake), and UDP scans (ICMP-based) immediately visible. Understanding *why* a scan needs root (raw socket access) matters more than just knowing it does.
3. **Hashing is a one-way function — cracking is about guessing, not reversing:** Whether using Hashcat's mask attacks or a custom Python `hashlib` script, the process is always the same: generate a candidate, hash it, compare. Weak inputs (short numbers, common passwords) fall in seconds regardless of how strong the hash algorithm is.

---

## Tools Used This Week
| Tool | Days Used | Comfort Level (1-5) |
|---|---|---|
| Bash | Day 01–06 | 4 |
| ip / ss / ping | Day 01 | 3 |
| tree / file / stat / find / cat | Day 02 | 4 |
| Nmap | Day 03 | 3 |
| Wireshark | Day 03 | 2 |
| useradd / usermod / groupadd | Day 04 | 3 |
| head / tail | Day 04 | 4 |
| md5sum | Day 05 | 4 |
| hashid / hash-identifier | Day 05 | 3 |
| hashcat | Day 05 | 3 |
| Python (hashlib) | Day 06 | 3 |

---

## Biggest Challenge
On Day 03, running `nmap -sS` without `sudo` silently fell back to a TCP Connect scan instead of the intended SYN scan. The root cause — SYN scanning requires raw socket access, which needs root or `CAP_NET_RAW` — was not immediately obvious. Verifying the scan behavior in Wireshark confirmed the issue. This highlighted that understanding the *privilege model* behind tools is as important as knowing the tool's syntax.

---

## Skill Progression
| Skill Area | Start of Week | End of Week |
|---|---|---|
| Linux CLI & Administration | Beginner | Comfortable |
| Networking & TCP/IP | Beginner | Intermediate |
| Network Scanning (Nmap) | No experience | Intermediate |
| Cryptography & Hashing | No experience | Intermediate |
| Bash Scripting | Beginner | Basic Automation |
| Python Scripting | Beginner | Basic Automation |

---

## Looking Ahead to Week 2
Week 2 will build on the foundation with deeper dives into applied workflows — combining tools (e.g., extracting hashes from network captures and cracking them offline), exploring web application security basics, and beginning to think like a defender by analyzing logs and firewall configurations.

---

*Week 1 | Foundation Week | Linux Administration, Networking, Cryptography*
