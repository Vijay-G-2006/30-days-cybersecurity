# Commands Cheatsheet

Quick-reference for commands used during the internship. Organized by domain.

> **Guideline:** Only add commands that were actually used and understood. This is a personal reference, not a bulk dump.

---

## Network Analysis

```bash
# ip — Interface and routing inspection (Day 01)
ip addr show                # View all interfaces with assigned IPs
ip link show                # View interface status (UP/DOWN)
ip route show               # View routing table and default gateway

# ss — Socket statistics (Day 01)
ss -tuln                    # List TCP/UDP listening ports (numeric)

# ping — Reachability testing (Day 01)
ping -c 4 192.0.2.1         # Send 4 ICMP echo requests

# curl — HTTP inspection (Day 01)
curl -I https://example.com # Fetch HTTP response headers only
```

```bash
# Nmap — Network scanning and discovery (Day 03)
nmap 192.0.2.1               # Basic TCP scan (top 1000 ports)
nmap -p 22,80,443 192.0.2.1  # Scan specific ports
nmap -p- 192.0.2.1           # Scan all 65,535 ports
sudo nmap -sS 192.0.2.1      # SYN scan (half-open, stealthier, requires root)
nmap -sT 192.0.2.1           # TCP Connect scan (full handshake)
sudo nmap -sU 192.0.2.1      # UDP scan (requires root)
nmap -sV 192.0.2.1           # Service version detection
nmap -sC 192.0.2.1           # Run default NSE scripts
sudo nmap -A 192.0.2.1       # Aggressive scan (OS, version, scripts, traceroute)
```

```bash
# tcpdump
# [Add commands as used]
```

---

## Linux Administration

```bash
# Filesystem navigation (Day 01)
pwd                         # Print working directory
ls -la                      # List all files with permissions
cd /path                    # Change directory
mkdir -p dir/subdir         # Create nested directories

# File operations (Day 01)
touch file.txt              # Create empty file
cp src dest                 # Copy file
mv old new                  # Move or rename file
rm -rf dir/                 # Remove directory recursively

# File permissions and ownership (Day 01)
chmod 755 script.sh         # Set rwxr-xr-x permissions
chmod u+x script.sh         # Add execute for owner
chown user:group file.txt   # Change ownership

# Process management (Day 01)
ps aux                      # List all running processes
top                         # Real-time process monitor
kill -9 <PID>               # Force terminate process
systemctl status <service>  # Check systemd service status

# System information (Day 01)
uname -a                    # Kernel and OS details
df -h                       # Disk usage (human-readable)
free -h                     # Memory usage (human-readable)

# Filesystem inspection (Day 02)
tree -L 1 --dirsfirst /     # Top-level directory overview
tree -L 2 --dirsfirst /etc  # Two-level view of a specific directory
file /path/to/file          # Identify file type by content
stat /path/to/file          # Detailed metadata (permissions, inode, timestamps)
find /etc -name "*.conf"    # Search for files by name pattern
cat /etc/passwd             # Display file contents

# User and group management (Day 04)
sudo useradd -m testuser    # Add user and create home directory
sudo useradd -M svc_account # Add user without home directory
sudo userdel -r testuser    # Delete user, home directory, and mail spool
sudo groupadd developers    # Create a new group
sudo groupdel developers    # Delete a group
sudo usermod -aG sudo user  # Append user to a secondary group
sudo usermod -s /bin/bash user # Set default shell for a user
sudo su testuser            # Switch to another user context

# File inspection and bash efficiency (Day 04)
head -n 5 /etc/passwd       # View the first 5 lines of a file
tail -n 5 /etc/passwd       # View the last 5 lines of a file
sudo !!                     # Execute the previous command with sudo
```

---

## Web Application Security

```bash
# curl / HTTP inspection
# [Add commands as used]
```

```bash
# Burp Suite / OWASP ZAP
# [Add commands as used]
```

---

## Defensive / Blue Team

```bash
# Firewall rules (iptables / ufw)
# [Add commands as used]
```

```bash
# Log analysis
# [Add commands as used]
```

---

## Offensive / Red Team

```bash
# Enumeration
# [Add commands as used]
```

```bash
# Exploitation
# [Add commands as used]
```

---

## Cryptography and Password Recovery

```bash
# Hash generation and identification (Day 05)
echo -n "hello" | md5sum    # Generate MD5 hash of a string (-n prevents trailing newline)
hashid <hash>               # Identify likely algorithms for an unknown hash
hash-identifier             # Interactive tool for identifying unknown hashes

# Hashcat — Password recovery (Day 05)
hashcat -m 0 -a 3 <hash> ?a?a?a?a?a  # Mask attack against an MD5 hash (5 chars)
hashcat -m 0 -a 0 <hashes.txt> <wordlist.txt> # Dictionary attack using a wordlist
hashcat -m 0 -a 1 <hashes.txt> dict1.txt dict2.txt # Combinator attack
hashcat -m 0 --show <hash>           # Show already cracked hash from potfile
```

---

*Add the Day number next to each command for cross-referencing with daily logs.*
