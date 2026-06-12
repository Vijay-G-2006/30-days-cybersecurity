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
| Wireshark | Packet capture and analysis | `wireshark` |

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

### Web Application Security
| Tool | Purpose | Key Command |
|---|---|---|
| — | — | `—` |

### Defensive / Monitoring
| Tool | Purpose | Key Command |
|---|---|---|
| — | — | `—` |

### Offensive / Pentesting
| Tool | Purpose | Key Command |
|---|---|---|
| — | — | `—` |

---

*Updated as new tools are encountered throughout the internship.*
