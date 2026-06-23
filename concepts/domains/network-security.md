# Network Security

Core concepts for understanding how networks operate, how to test them, and how to defend them.

## TCP/IP Layer Model

The fundamental framework that governs all internet communication.

- [TCP/IP Model](../concepts-glossary.md#tcpip-model) — Four-layer model (Application, Transport, Internet, Network Access)
- [IPv4 Address](../concepts-glossary.md#ipv4-address) — 32-bit host identifiers in dotted-decimal notation
- [Private IP Address](../concepts-glossary.md#private-ip-address) — RFC 1918 reserved ranges (10.x, 172.16-31.x, 192.168.x.x)
- [Loopback Address](../concepts-glossary.md#loopback-address) — 127.0.0.1 for local testing
- [NAT (Network Address Translation)](../concepts-glossary.md#nat-network-address-translation) — Mapping private to public IPs

## Transport Layer Protocols

How data is reliably (or quickly) delivered between hosts.

- [TCP (Transmission Control Protocol)](../concepts-glossary.md#tcp-transmission-control-protocol) — Connection-oriented, reliable delivery
- [UDP (User Datagram Protocol)](../concepts-glossary.md#udp-user-datagram-protocol) — Connectionless, fast but unreliable

## Network Discovery & Scanning

Tools and techniques for identifying active hosts, open ports, and services.

- [SYN Scan (-sS)](../concepts-glossary.md#syn-scan--ss) — Half-open TCP scan technique
- [TCP Connect Scan (-sT)](../concepts-glossary.md#tcp-connect-scan--st) — Full-handshake port scan
- [UDP Scan (-sU)](../concepts-glossary.md#udp-scan--su) — Connectionless port scanning
- [Nmap Scripting Engine (NSE)](../concepts-glossary.md#nmap-scripting-engine-nse) — Advanced vulnerability detection via Lua scripts

**Related Tools:** [nmap](#nmap), [wireshark](#wireshark), [tshark](#tshark)

## Traffic Analysis & Packet Inspection

Capturing and analyzing network traffic for security insights.

- [Display Filter (Wireshark)](../concepts-glossary.md#display-filter-wireshark) — Post-capture filtering by protocol
- [Capture Filter (BPF)](../concepts-glossary.md#capture-filter-bpf) — Pre-capture limiting of recorded packets
- [TCP Stream Reassembly](../concepts-glossary.md#tcp-stream-reassembly) — Reconstructing full conversations from packets
- [Cleartext Credential Exposure](../concepts-glossary.md#cleartext-credential-exposure) — Passwords visible in unencrypted protocols
- [Passive OS Fingerprinting](../concepts-glossary.md#passive-os-fingerprinting) — Identifying OS via TCP/IP stack characteristics
- [Network Anomaly Detection](../concepts-glossary.md#network-anomaly-detection) — Statistical analysis for suspicious patterns

**Related Tools:** [wireshark](#wireshark), [tshark](#tshark)

## Denial of Service (DoS) Attacks & Mitigation

Techniques for overwhelming systems and defenses against them.

- [Denial of Service (DoS)](../concepts-glossary.md#denial-of-service-dos) — Resource exhaustion attacks
- [Distributed Denial of Service (DDoS)](../concepts-glossary.md#distributed-denial-of-service-ddos) — Multi-source DoS attacks
- [SYN Flood](../concepts-glossary.md#syn-flood) — TCP handshake exhaustion attack
- [UDP Flood](../concepts-glossary.md#udp-flood) — UDP packet bombardment
- [Application-layer DoS](../concepts-glossary.md#application-layer-dos) — HTTP connection exhaustion
- [SYN Cookies](../concepts-glossary.md#syn-cookies) — Kernel-level SYN flood mitigation
- [Rate Limiting](../concepts-glossary.md#rate-limiting) — Traffic throttling to prevent overload

**Related Tools:** [hping3](#hping3), [slowloris](#slowloris), [iptables](#iptables), [sysctl](#sysctl)

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 01 | TCP/IP Model, IPv4, TCP, UDP, Private IP, NAT, Loopback |
| Day 03 | SYN Scan, TCP Connect Scan, UDP Scan, NSE |
| Day 08 | Display Filter, Capture Filter, TCP Stream Reassembly, Cleartext Exposure, OS Fingerprinting, Anomaly Detection |
| Day 10 | DoS, DDoS, SYN Flood, UDP Flood, App-layer DoS, SYN Cookies, Rate Limiting |

---

## See Also

- [Linux Systems](linux-systems.md) — OS foundations for network configuration
- [Cryptography](cryptography.md) — Securing network traffic
- [Web Security](web-security.md) — Application-layer network attacks
- [All domains](../INDEX.md) — All domains
