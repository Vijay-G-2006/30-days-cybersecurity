# Network Security

Core concepts for understanding how networks operate, how to test them, and how to defend them.

## TCP/IP Layer Model

The fundamental framework that governs all internet communication.

- [[concepts-glossary#TCP/IP Model]] — Four-layer model (Application, Transport, Internet, Network Access)
- [[concepts-glossary#IPv4 Address]] — 32-bit host identifiers in dotted-decimal notation
- [[concepts-glossary#Private IP Address]] — RFC 1918 reserved ranges (10.x, 172.16-31.x, 192.168.x.x)
- [[concepts-glossary#Loopback Address]] — 127.0.0.1 for local testing
- [[concepts-glossary#NAT (Network Address Translation)]] — Mapping private to public IPs

## Transport Layer Protocols

How data is reliably (or quickly) delivered between hosts.

- [[concepts-glossary#TCP (Transmission Control Protocol)]] — Connection-oriented, reliable delivery
- [[concepts-glossary#UDP (User Datagram Protocol)]] — Connectionless, fast but unreliable

## Network Discovery & Scanning

Tools and techniques for identifying active hosts, open ports, and services.

- [[concepts-glossary#SYN Scan (-sS)]] — Half-open TCP scan technique
- [[concepts-glossary#TCP Connect Scan (-sT)]] — Full-handshake port scan
- [[concepts-glossary#UDP Scan (-sU)]] — Connectionless port scanning
- [[concepts-glossary#Nmap Scripting Engine (NSE)]] — Advanced vulnerability detection via Lua scripts

**Related Tools:** [[#nmap]], [[#wireshark]], [[#tshark]]

## Traffic Analysis & Packet Inspection

Capturing and analyzing network traffic for security insights.

- [[concepts-glossary#Display Filter (Wireshark)]] — Post-capture filtering by protocol
- [[concepts-glossary#Capture Filter (BPF)]] — Pre-capture limiting of recorded packets
- [[concepts-glossary#TCP Stream Reassembly]] — Reconstructing full conversations from packets
- [[concepts-glossary#Cleartext Credential Exposure]] — Passwords visible in unencrypted protocols
- [[concepts-glossary#Passive OS Fingerprinting]] — Identifying OS via TCP/IP stack characteristics
- [[concepts-glossary#Network Anomaly Detection]] — Statistical analysis for suspicious patterns

**Related Tools:** [[#wireshark]], [[#tshark]]

## Denial of Service (DoS) Attacks & Mitigation

Techniques for overwhelming systems and defenses against them.

- [[concepts-glossary#Denial of Service (DoS)]] — Resource exhaustion attacks
- [[concepts-glossary#Distributed Denial of Service (DDoS)]] — Multi-source DoS attacks
- [[concepts-glossary#SYN Flood]] — TCP handshake exhaustion attack
- [[concepts-glossary#UDP Flood]] — UDP packet bombardment
- [[concepts-glossary#Application-layer DoS]] — HTTP connection exhaustion
- [[concepts-glossary#SYN Cookies]] — Kernel-level SYN flood mitigation
- [[concepts-glossary#Rate Limiting]] — Traffic throttling to prevent overload

**Related Tools:** [[#hping3]], [[#slowloris]], [[#iptables]], [[#sysctl]]

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 01 | TCP/IP Model, IPv4, TCP, UDP, Private IP, NAT, Loopback |
| Day 03 | SYN Scan, TCP Connect Scan, UDP Scan, NSE |
| Day 08 | Display Filter, Capture Filter, TCP Stream Reassembly, Cleartext Exposure, OS Fingerprinting, Anomaly Detection |
| Day 10 | DoS, DDoS, SYN Flood, UDP Flood, App-layer DoS, SYN Cookies, Rate Limiting |

---

## See Also

- [[linux-systems]] — OS foundations for network configuration
- [[cryptography]] — Securing network traffic
- [[web-security]] — Application-layer network attacks
- [[concepts/INDEX]] — All domains
