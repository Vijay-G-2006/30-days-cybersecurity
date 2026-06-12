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

---

## By Category

### Network Analysis
| Tool | Purpose | Key Command |
|---|---|---|
| ip | Interface and route inspection | `ip addr show` |
| ss | Active connections and listening ports | `ss -tuln` |
| ping | Network reachability testing | `ping -c 4 <target>` |
| curl | HTTP request and header inspection | `curl -I <url>` |

### Linux / System
| Tool | Purpose | Key Command |
|---|---|---|
| Bash | Shell interaction and scripting | `bash` |
| tree | Recursive directory visualization | `tree -L 2 --dirsfirst /path` |
| file | File type identification | `file /path/to/file` |
| stat | File metadata inspection | `stat /path/to/file` |
| find | Filesystem search and filtering | `find /path -name "*.conf"` |
| cat | File content display | `cat /etc/passwd` |

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
