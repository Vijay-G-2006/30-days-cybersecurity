# Concepts Glossary

Terms and concepts defined during the internship. Definitions should be written in own words, not copied from textbooks.

> **Obsidian note:** Each term can be linked from daily logs using `[[concepts-glossary#Term]]` for cross-referencing.

---

## Glossary

| # | Term | Domain | Definition (in own words) | Day Learned |
|---|---|---|---|---|
| 1 | TCP/IP Model | Network Security | A four-layer networking model (Application, Transport, Internet, Network Access) that defines how data is packaged, addressed, routed, and delivered across the internet. It is the practical model the internet actually runs on, unlike the theoretical OSI model. | Day 01 |
| 2 | IPv4 Address | Network Security | A 32-bit numerical identifier assigned to each device on a network, written as four octets separated by dots (e.g., 192.168.1.10). Each octet ranges from 0 to 255. | Day 01 |
| 3 | TCP (Transmission Control Protocol) | Network Security | A connection-oriented transport protocol that uses a three-way handshake (SYN, SYN-ACK, ACK) to establish reliable, ordered data delivery between two hosts. | Day 01 |
| 4 | UDP (User Datagram Protocol) | Network Security | A connectionless transport protocol that sends data without establishing a connection or guaranteeing delivery. Faster than TCP but unreliable; used by DNS, DHCP, and streaming. | Day 01 |
| 5 | Private IP Address | Network Security | An IP address from the RFC 1918 reserved ranges (10.x.x.x, 172.16-31.x.x, 192.168.x.x) that is not routable on the public internet. Used within internal networks and requires NAT for external communication. | Day 01 |
| 6 | NAT (Network Address Translation) | Network Security | A technique used by routers to map private internal IP addresses to a single public IP address, allowing multiple devices to share one public IP for internet access. | Day 01 |
| 7 | Loopback Address | Network Security | The reserved IP address 127.0.0.1 that refers to the local machine itself. Traffic sent to this address never leaves the network interface; commonly used for testing local services. | Day 01 |
| 8 | File Permissions (Linux) | Linux / Operating Systems | A three-tier access control system (owner, group, others) with three permission types (read=4, write=2, execute=1) expressed in octal notation. Controls who can read, modify, or execute a file. | Day 01 |
| 9 | Filesystem Hierarchy Standard (FHS) | Linux / Operating Systems | The formal specification that defines the directory structure of Linux systems — which directories exist at the top level, what each contains, and why the separation exists. Maintained by the Linux Foundation. | Day 02 |
| 10 | /etc (Configuration Directory) | Linux / Operating Systems | The central directory for all system-wide configuration files. Contains passwd, shadow, fstab, sudoers, and service-specific configs. Misconfiguration here is a common vector for privilege escalation. | Day 02 |
| 11 | /proc (Virtual Filesystem) | Linux / Operating Systems | A kernel-generated virtual filesystem that exposes real-time process information and system statistics as readable files. Does not exist on disk; each running process gets a numbered directory under /proc. | Day 02 |
| 12 | /dev (Device Files) | Linux / Operating Systems | A directory of special files representing hardware devices and virtual interfaces. Linux treats devices as files, enabling standard read/write operations on hardware. Includes /dev/null, /dev/urandom, and disk device nodes. | Day 02 |
| 13 | Sticky Bit | Linux / Operating Systems | A special permission flag (represented as 't' in the permission string) applied to directories like /tmp. It prevents users from deleting files they do not own, even in world-writable directories. | Day 02 |
| 14 | SYN Scan (-sS) | Network Security | A "half-open" TCP scan that sends a SYN packet and waits for a SYN-ACK, but resets (RST) the connection before completing the three-way handshake. Faster and stealthier than a full connect scan. | Day 03 |
| 15 | TCP Connect Scan (-sT) | Network Security | A port scan that completes the full TCP three-way handshake. Slower and more easily logged by target systems, but does not require raw socket access (root privileges). | Day 03 |
| 16 | UDP Scan (-sU) | Network Security | A scan targeting connectionless UDP ports. Relies on ICMP Port Unreachable messages to determine if a port is closed, making it generally slower and less definitive than TCP scanning. | Day 03 |
| 17 | Nmap Scripting Engine (NSE) | Network Security | A feature of Nmap that allows users to write and execute Lua scripts for advanced network discovery, vulnerability detection, and exploitation during a scan. | Day 03 |
| 18 | UID / GID | Linux / Operating Systems | User Identifier and Group Identifier. The numerical values Linux actually uses to track identity and permissions. UIDs under 1000 are reserved for system and service accounts, while 1000+ are for human users. | Day 04 |
| 19 | /usr/local/bin | Linux / Operating Systems | The standard directory for locally compiled binaries and custom administrative scripts. Placing scripts here allows them to be executed as system commands without conflicting with package-managed software in /usr/bin. | Day 04 |
| 20 | History Expansion (!!) | Linux / Operating Systems | A bash shell feature that substitutes the last executed command into the current prompt. Extremely useful for re-running a command that failed due to missing privileges (e.g., `sudo !!`). | Day 04 |
| 21 | Cryptographic Hashing | Cryptography | A one-way deterministic mathematical function that takes an input of any size and produces a fixed-size output. Used for password storage and file integrity. | Day 05 |
| 22 | Collision Resistance | Cryptography | A property of secure hash functions where it is computationally infeasible to find two different inputs that produce the same hash output. | Day 05 |
| 23 | Mask Attack (Hashcat -a 3) | Cryptography | A highly optimized password cracking technique where candidates are generated based on a known or assumed pattern (e.g., lowercase followed by 4 digits), vastly reducing the keyspace compared to blind brute-forcing. | Day 05 |
| 24 | Dictionary Attack (Hashcat -a 0) | Cryptography | A password cracking technique that hashes every word in a provided wordlist (like rockyou.txt) and compares the output against the target hashes. | Day 05 |
| 25 | Combinator Attack (Hashcat -a 1) | Cryptography | A password cracking technique that combines words from two different dictionaries by appending each word from the second list to each word in the first list. | Day 05 |
| 26 | Python hashlib | Cryptography | A built-in Python library that provides a common interface to many secure hash and message digest algorithms. | Day 06 |
| 27 | Brute-Force Attack (Hashing) | Cryptography | The process of guessing the original input of a hash by generating many potential inputs, hashing them, and comparing the result to the target hash. | Day 06 |
| 28 | Intercepting Proxy | Web Security | A tool that sits between a browser and a web server, capturing all HTTP/HTTPS traffic for inspection, modification, and replay before forwarding it to the destination. | Day 07 |
| 29 | Burp Repeater | Web Security | A Burp Suite module that allows manual modification and re-sending of individual HTTP requests to observe how the server responds to different inputs. | Day 07 |
| 30 | Burp Intruder | Web Security | A Burp Suite module for automated, customizable attacks that iterates through payload lists against defined insertion points in HTTP requests. | Day 07 |
| 31 | Intruder Attack Types (Sniper, Battering Ram, Pitchfork, Cluster Bomb) | Web Security | Four distinct payload iteration strategies in Burp Intruder, ranging from single-position sequential testing (Sniper) to exhaustive Cartesian-product combinations across multiple positions (Cluster Bomb). | Day 07 |
| 32 | Response Size Analysis | Web Security | The technique of identifying successful attack payloads by comparing HTTP response body lengths — the outlier size among uniform results typically indicates a different server-side outcome (e.g., a successful login vs. a failed one). | Day 07 |
| 33 | Deliberately Vulnerable Application | Web Security | A purpose-built, intentionally insecure application or VM (like DVWA or Metasploitable 2) used as a legal, safe target for practicing penetration testing techniques in an isolated lab environment. | Day 07 |
| 34 | HTTP Header Information Leakage | Web Security | The exposure of sensitive server-side details (web server version, language runtime, OS) through HTTP response headers like Server, X-Powered-By, which aids attackers in targeted vulnerability research. | Day 07 |

---

## Concepts by Domain

### Network Security
- **TCP/IP Model** — Four-layer model governing internet communication (Day 01)
- **IPv4 Address** — 32-bit host identifier in dotted-decimal notation (Day 01)
- **TCP** — Reliable, connection-oriented transport protocol (Day 01)
- **UDP** — Fast, connectionless transport protocol (Day 01)
- **Private IP Address** — Non-routable internal network address per RFC 1918 (Day 01)
- **NAT** — Private-to-public IP translation at the router level (Day 01)
- **Loopback Address** — 127.0.0.1, self-referencing local address (Day 01)
- **SYN Scan (-sS)** — Half-open TCP port scanning technique (Day 03)
- **TCP Connect Scan (-sT)** — Full-handshake TCP port scanning technique (Day 03)
- **UDP Scan (-sU)** — Connectionless port scanning technique (Day 03)
- **Nmap Scripting Engine (NSE)** — Lua-based script execution framework for Nmap (Day 03)

### Linux / Operating Systems
- **File Permissions** — Octal-based access control for files and directories (Day 01)
- **Filesystem Hierarchy Standard (FHS)** — Formal specification defining Linux directory structure and purpose (Day 02)
- **/etc** — Central system configuration directory; security-critical (Day 02)
- **/proc** — Virtual filesystem exposing live process and kernel data (Day 02)
- **/dev** — Device files enabling file-based hardware interaction (Day 02)
- **Sticky Bit** — Permission flag preventing unauthorized file deletion in shared directories (Day 02)
- **UID / GID** — Numerical identifiers for users and groups (Day 04)
- **/usr/local/bin** — Standard path for custom scripts and local binaries (Day 04)
- **History Expansion (!!)** — Bash feature to recall the previous command (Day 04)

### Web Security
- **Intercepting Proxy** — Tool capturing HTTP/HTTPS traffic between browser and server for analysis (Day 07)
- **Burp Repeater** — Module for manually modifying and resending HTTP requests (Day 07)
- **Burp Intruder** — Module for automated payload-based attacks against HTTP parameters (Day 07)
- **Intruder Attack Types** — Sniper, Battering Ram, Pitchfork, Cluster Bomb strategies for payload iteration (Day 07)
- **Response Size Analysis** — Identifying successful payloads by spotting response length anomalies (Day 07)
- **Deliberately Vulnerable Application** — Purpose-built insecure targets for legal security practice (Day 07)
- **HTTP Header Information Leakage** — Sensitive server details exposed via response headers (Day 07)

### Cryptography
- **Cryptographic Hashing** — One-way deterministic function for generating fixed-size digests (Day 05)
- **Collision Resistance** — The difficulty of finding two inputs that produce the same hash (Day 05)
- **Mask Attack (-a 3)** — Optimized brute-force attack using character pattern masks (Day 05)
- **Dictionary Attack (-a 0)** — Password recovery using a predefined list of words (Day 05)
- **Combinator Attack (-a 1)** — Password recovery combining words from two dictionaries (Day 05)
- **Python hashlib** — Built-in Python library for cryptographic hashing (Day 06)
- **Brute-Force Attack (Hashing)** — Guessing an input by continuously hashing and comparing outputs (Day 06)

### Defensive Security (Blue Team)
- *Add concepts as encountered*

### Offensive Security (Red Team)
- *Add concepts as encountered*

### Compliance and Governance
- *Add concepts as encountered*

---

*Target: 24+ terms by Day 24 — approximately one new concept per day.*
