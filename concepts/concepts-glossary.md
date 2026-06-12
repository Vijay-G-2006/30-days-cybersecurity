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
- *Add concepts as encountered*

### Cryptography
- *Add concepts as encountered*

### Defensive Security (Blue Team)
- *Add concepts as encountered*

### Offensive Security (Red Team)
- *Add concepts as encountered*

### Compliance and Governance
- *Add concepts as encountered*

---

*Target: 24+ terms by Day 24 — approximately one new concept per day.*
