# Linux & Operating Systems

Foundational knowledge of Linux system administration, file permissions, process management, and operating system internals.

## Filesystem & Directory Structure

How Linux organizes data and configuration.

- [Filesystem Hierarchy Standard (FHS)](../concepts-glossary.md#filesystem-hierarchy-standard-fhs) — Formal specification of Linux directory structure
- [/etc (Configuration Directory)](../concepts-glossary.md#etc-configuration-directory) — System-wide configuration files
- [/proc (Virtual Filesystem)](../concepts-glossary.md#proc-virtual-filesystem) — Real-time process and system statistics
- [/dev (Device Files)](../concepts-glossary.md#dev-device-files) — Hardware and virtual device interfaces
- [/usr/local/bin](../concepts-glossary.md#usrlocalbin) — Directory for custom and locally compiled binaries

## File Permissions & Access Control

How Linux enforces who can read, write, and execute files.

- [File Permissions (Linux)](../concepts-glossary.md#file-permissions-linux) — Owner/group/other + read/write/execute model (octal notation)
- [Sticky Bit](../concepts-glossary.md#sticky-bit) — Prevents non-owners from deleting files in shared directories like /tmp

## User & Group Management

Identity and access control at the OS level.

- [UID / GID](../concepts-glossary.md#uid--gid) — Numerical user and group identifiers used internally by the kernel
- Users and groups are the basis for privilege escalation and lateral movement

## Shell Features & Scripting

Interactive shell and command-line productivity.

- [History Expansion (!!!)](../concepts-glossary.md#history-expansion-) — Re-run last command with `sudo !!`
- Bash scripting enables automation of system administration tasks

## Concepts by Day Introduced

| Day | Concepts |
|-----|----------|
| Day 01 | File Permissions, FHS |
| Day 02 | /etc, /proc, /dev, Sticky Bit |
| Day 04 | UID/GID, /usr/local/bin, History Expansion |

---

## See Also

- [Network Security](network-security.md) — Network configuration on Linux
- [Cryptography](cryptography.md) — Hashing and password security in Linux
- [Offensive Security](offensive-security.md) — Post-exploitation and privilege escalation
- [All domains](../INDEX.md) — All domains
