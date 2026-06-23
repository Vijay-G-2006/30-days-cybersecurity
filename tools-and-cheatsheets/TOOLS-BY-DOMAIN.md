# Tools Organized by Domain

Tools and commands organized by the cybersecurity domains where they're applied. See [tools-index.md](tools-index.md) for the full alphabetical listing.

## Network Security & Analysis

### Discovery & Scanning
- [[#Nmap]] — Network discovery and port scanning with scripting
- [[#ip (iproute2)]] — Network interface configuration and inspection
- [[#ss (iproute2)]] — Socket statistics and listening port analysis

### Traffic Capture & Analysis
- [[#Wireshark]] — GUI packet capture and protocol analysis
- [[#tshark]] — CLI packet capture for scripted analysis
- [[#tcpdump]] — Low-level packet capture utility

### Packet Generation & DoS Testing
- [[#hping3]] — Custom packet crafting and SYN flood simulation
- [[#Slowloris]] — Application-layer HTTP DoS tool
- [[#curl]] — HTTP requests and header inspection
- [[#ping]] — ICMP reachability testing

### Mitigation & Firewall
- [[#iptables]] — Netfilter firewall for packet filtering and rate limiting
- [[#sysctl]] — Kernel parameter tuning for network defense

---

## Linux & System Administration

### System Inspection
- [[#Bash]] — Default shell and scripting environment
- [[#tree]] — Recursive directory visualization
- [[#file]] — File type identification by content
- [[#stat]] — File metadata inspection
- [[#find]] — Filesystem search and filtering
- [[#cat]] — File content display
- [[#head]] — View start of file
- [[#tail]] — View end of file

### User & Permission Management
- [[#useradd]] — Create new users
- [[#userdel]] — Delete users
- [[#groupadd]] — Create groups
- [[#groupdel]] — Delete groups
- [[#usermod]] — Modify user accounts
- [[#su]] — Switch user identity

---

## Cryptography & Password Recovery

### Hashing
- [[#md5sum]] — MD5 checksum computation
- [[#hashid]] — Hash type identification
- [[#hash-identifier]] — Hash type identification tool
- [[#Python (hashlib)]] — Built-in hash generation library

### Password Cracking
- [[#hashcat]] — GPU-accelerated password recovery (dictionary, brute-force, mask, combinator attacks)

---

## Web Application Security

### Intercepting Proxy & Testing
- [[#Burp Suite (Community Edition)]] — HTTP interception, Repeater, Intruder, scanning
- Used for manual request modification and automated fuzzing

### Vulnerable Testing Targets
- [[#Metasploitable 2]] — Deliberately vulnerable Linux VM
- [[#DVWA]] — Damn Vulnerable Web Application (if used)
- [[#VirtualBox]] — Hypervisor for lab VMs

---

## Social Engineering

### Phishing Tools
- [[#Zphisher]] — Phishing page generator with 30+ templates
- [[#SET (Social Engineering Toolkit)]] — Live website cloning and credential harvesting
- [[#Ngrok]] — Secure tunnel for exposing local servers to the internet

---

## Offensive Security & Exploitation

### Exploitation Frameworks
- [[#Metasploit Framework]] — Modular exploitation platform
- [[#msfconsole]] — Interactive Metasploit console
- [[#msfvenom]] — Payload generation and encoding
- [[#Meterpreter]] — Advanced interactive payload for post-exploitation

### Brute-Force & Cracking
- [[#Hydra]] — Multi-protocol brute-force authentication
- [[#Medusa]] — Parallel remote login brute-forcing
- [[#Ncrack]] — High-speed network authentication cracker
- [[#Patator]] — Flexible brute-force automation

### Database & Injection
- [[#MySQL (Server)]] — Relational database server
- [[#mysql (Client)]] — MySQL client for queries and schema inspection
- [[#sqlmap]] — Automated SQL injection detection and exploitation

---

## Database & Backend

### Data Storage & Query
- [[#MySQL (Server)]] — Relational database for application backends
- [[#mysql (Client)]] — Query and schema inspection tool

---

## Virtualization & Lab Infrastructure

### Hypervisor
- [[#VirtualBox]] — VM creation and management for isolated testing environments

---

## Tools by Day Introduced

| Day | New Tools | Domain |
|-----|-----------|--------|
| Day 01 | Bash, ip, ss, ping, curl | Linux / Network |
| Day 02 | tree, file, stat, find, cat | Linux |
| Day 03 | Nmap, Wireshark | Network |
| Day 04 | useradd, userdel, groupadd, groupdel, usermod, su, head, tail | Linux |
| Day 05 | md5sum, hashid, hash-identifier, hashcat | Cryptography |
| Day 06 | Python (hashlib) | Cryptography |
| Day 07 | Burp Suite, Metasploitable 2, VirtualBox | Web Security / Lab |
| Day 08 | tshark | Network |
| Day 09 | Zphisher, SET, Ngrok | Social Engineering |
| Day 10 | hping3, Slowloris, iptables, sysctl | Network / Offensive |
| Day 11 | Metasploit Framework, msfconsole, msfvenom | Offensive |
| Day 12 | Hydra, Medusa, Ncrack, Patator | Offensive |
| Day 13 | MySQL Server, mysql Client | Database |
| Day 14 | sqlmap | Database / Web Security |

---

## See Also

- [Tools Index (alphabetical)](tools-index.md)
- [Concepts by domain](../concepts/INDEX.md)
- [Daily logs by domain](../daily-logs/INDEX.md)
- [← Return to main index](../INDEX.md)
