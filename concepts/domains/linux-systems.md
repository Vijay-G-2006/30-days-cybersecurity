# Linux & Operating Systems

Foundational knowledge of Linux system administration, file permissions, process management, and operating system internals.

## Filesystem & Directory Structure

How Linux organizes data and configuration.

- [[concepts-glossary#Filesystem Hierarchy Standard (FHS)]] — Formal specification of Linux directory structure
- [[concepts-glossary#/etc (Configuration Directory)]] — System-wide configuration files
- [[concepts-glossary#/proc (Virtual Filesystem)]] — Real-time process and system statistics
- [[concepts-glossary#/dev (Device Files)]] — Hardware and virtual device interfaces
- [[concepts-glossary#/usr/local/bin]] — Directory for custom and locally compiled binaries

## File Permissions & Access Control

How Linux enforces who can read, write, and execute files.

- [[concepts-glossary#File Permissions (Linux)]] — Owner/group/other + read/write/execute model (octal notation)
- [[concepts-glossary#Sticky Bit]] — Prevents non-owners from deleting files in shared directories like /tmp

## User & Group Management

Identity and access control at the OS level.

- [[concepts-glossary#UID / GID]] — Numerical user and group identifiers used internally by the kernel
- Users and groups are the basis for privilege escalation and lateral movement

## Shell Features & Scripting

Interactive shell and command-line productivity.

- [[concepts-glossary#History Expansion (!!!)]] — Re-run last command with `sudo !!`
- Bash scripting enables automation of system administration tasks

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 01 | File Permissions, FHS |
| Day 02 | /etc, /proc, /dev, Sticky Bit |
| Day 04 | UID/GID, /usr/local/bin, History Expansion |

---

## See Also

- [[network-security]] — Network configuration on Linux
- [[cryptography]] — Hashing and password security in Linux
- [[offensive-security]] — Post-exploitation and privilege escalation
- [[concepts/INDEX]] — All domains
