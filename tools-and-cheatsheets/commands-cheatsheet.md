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
# Wireshark — Display filters (Day 08)
# (Typed into the filter bar after capture has started)
ip.addr == 192.0.2.10                     # All traffic to/from an IP
ip.src == 192.0.2.10                      # Only traffic FROM this IP
ip.dst == 192.0.2.10                      # Only traffic TO this IP
tcp.port == 80                            # TCP traffic on port 80
tcp.dstport == 443                        # TCP destined for port 443
udp.port == 53                            # DNS traffic
http.request.method == "POST"             # HTTP POST requests (login forms)
tcp.flags.syn == 1 && tcp.flags.ack == 1  # SYN-ACK → reveals OPEN ports
tcp.flags.syn == 1 && tcp.flags.ack == 0  # SYN only → connection attempts
dns.qry.name contains "example"           # DNS queries for a domain
http.server                               # Packets with Server header (version info)
ftp.request.command == "USER" || ftp.request.command == "PASS"  # FTP credentials
tcp.stream eq 5                           # Follow a specific TCP conversation
```

```bash
# Wireshark — Capture filters / BPF syntax (Day 08)
# (Set BEFORE capture starts — non-matching packets are permanently discarded)
host 192.0.2.10                           # Traffic to/from specific IP
port 80                                   # Traffic on port 80
net 192.0.2.0/24                          # Traffic on a subnet
tcp                                       # TCP only
not arp                                   # Exclude ARP
host 192.0.2.10 and port 443              # Combined filter
```

```bash
# tshark — CLI packet analysis (Day 08)
tshark -i eth0 -c 100                     # Capture 100 packets
tshark -i eth0 -Y "http"                  # Capture with display filter
tshark -r capture.pcapng -Y "ip.addr == 192.0.2.10"  # Read file + filter
tshark -r capture.pcapng -Y "tcp.flags.syn==1 && tcp.flags.ack==1" \
  -T fields -e ip.src -e tcp.srcport      # Extract open ports (like nmap)
tshark -r capture.pcapng -q -z io,phs     # Protocol hierarchy statistics
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
# Burp Suite — Setup and proxy configuration (Day 07)
# 1. Launch Burp Suite (listens on 127.0.0.1:8080 by default)
burpsuite &

# 2. Configure Firefox: Settings → Network → Manual Proxy → 127.0.0.1:8080
# 3. Install Burp CA cert: browse to http://burp → download cacert.der → import into Firefox

# Burp Suite — Core workflow (Day 07)
# Proxy → Intercept is on   → catch and modify live requests before forwarding
# Proxy → HTTP history      → review all past requests/responses (even with intercept off)
# Right-click request → Send to Repeater  → manually modify and resend
# Right-click request → Send to Intruder  → set payload positions with § markers

# Burp Intruder — Attack types (Day 07)
# Sniper:        Single payload list, one position at a time
# Battering Ram:  Single payload list, same value in all positions simultaneously
# Pitchfork:     One list per position, iterated in parallel (pair 1, pair 2, ...)
# Cluster Bomb:  One list per position, every combination (Cartesian product)

# Burp Intruder — Results analysis (Day 07)
# Sort by "Length" column → the response size that differs from the majority = likely success
# Sort by "Status" column → look for 302 redirects among 200 responses
```

```bash
# Metasploitable 2 — Lab target setup (Day 07)
# Import .vmdk into VirtualBox → set network to Host-Only → boot
# Default credentials: msfadmin / msfadmin
# Access web apps: http://<metasploitable-ip>/
# DVWA login: http://<metasploitable-ip>/dvwa/login.php (admin / password)
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

## Social Engineering / Phishing

```bash
# Zphisher — Automated phishing page generator (Day 09)
git clone https://github.com/htr-tech/zphisher.git  # Clone the repository
chmod +x zphisher.sh                                 # Make executable
bash zphisher.sh                                     # Launch Zphisher
# Select template (e.g., 03 for Google) → set port → phishing page served
# Credentials captured in auth/usernames.dat
```

```bash
# SET (Social Engineering Toolkit) — Credential Harvester (Day 09)
sudo setoolkit                                        # Launch SET (requires root)
# Navigate: 1 → Social-Engineering Attacks
#           2 → Website Attack Vectors
#           3 → Credential Harvester Attack Method
#           2 → Site Cloner
# Enter attacker IP → Enter URL to clone → Harvester starts on port 80
# Credentials saved to /root/.set/reports/
```

```bash
# Ngrok — Tunnel local server to the internet (Day 09)
ngrok config add-authtoken <YOUR_AUTH_TOKEN>           # One-time authentication
ngrok http 80                                         # Expose port 80 publicly
ngrok http 8080                                       # Expose port 8080 publicly
# Provides a public https://xxxx.ngrok-free.app URL forwarding to localhost
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

```python
# Python hashlib — Custom hash automation (Day 06)
import hashlib
hashlib.sha512("input".encode('utf-8')).hexdigest()  # Generate SHA-512 hash
hashlib.sha256("input".encode('utf-8')).hexdigest()  # Generate SHA-256 hash
hashlib.md5("input".encode('utf-8')).hexdigest()     # Generate MD5 hash
```

---

*Add the Day number next to each command for cross-referencing with daily logs.*
