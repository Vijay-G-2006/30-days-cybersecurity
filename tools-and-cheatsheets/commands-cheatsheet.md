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
# Nmap
# [Add commands as used]
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

## Cryptography and Certificates

```bash
# OpenSSL
# [Add commands as used]
```

---

*Add the Day number next to each command for cross-referencing with daily logs.*
