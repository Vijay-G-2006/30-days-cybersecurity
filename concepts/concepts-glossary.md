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

### Linux / Operating Systems
- **File Permissions** — Octal-based access control for files and directories (Day 01)

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
