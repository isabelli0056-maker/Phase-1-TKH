# Phase 1: Linux Discovery & System Hardening
### Innovation Fellowship | Week 1 Lab Artifacts

This repository contains the core technical artifacts developed during the first week of Phase 1. The focus was on mastering the Linux filesystem, automating access control, and performing stream-based log analysis for threat detection.

---

## 🛠️ Project Components

### 1. File System Navigation (`discovery.txt`)
**Objective:** Map restricted system directories and perform a forensic "scavenger hunt" to extract hidden intelligence.
* **Key Skills:** Directory traversal, absolute vs. relative paths, and hidden file identification.
* **Workflow:**
    * Navigated to `/var/log` to analyze system behavior.
    * Accessed `/opt/alpha` to retrieve mission-critical parameters.
    * Uncovered hidden tokens within `/var/tmp/.blackout`.

### 2. Access Control Automation (`harden.sh`)
**Objective:** Implement the **Principle of Least Privilege** by automating permission changes for sensitive directories and files.
* **Key Skills:** Permission octal codes (`chmod`), ownership management (`chown`), and security auditing.
* **Access Matrix:**

| Target | Command | Resulting Permissions |
| :--- | :--- | :--- |
| `~/Vault` | `chmod 700` | Owner-only Access (rwx------) |
| `secrets.txt` | `chmod 600` | Owner Read/Write (rw-------) |
| `/etc/shadow` | `chmod 640` | Secure User Credential Storage |

### 3. Threat Intelligence & Log Analysis (`threat_ips.txt`)
**Objective:** Utilize the "Holy Trinity" of Linux text processing (**grep**, **awk**, and **sed**) to parse attack logs and identify malicious actors.
* **Key Skills:** Regular Expressions (Regex), pipe-lining, and data deduplication.
* **Analysis Logic:** 1. Filtered `access.log` for SQL Injection patterns (e.g., `UNION SELECT`).
    2. Isolated attacker IP addresses using `awk`.
    3. Exported a unique, sorted list of threats for firewall blacklisting.

---

## 🧠 Technical Summary
This lab sequence demonstrated the power of the **Linux Command Line Interface (CLI)** as a primary tool for security administration. By leveraging standard streams (`stdin`, `stdout`, `stderr`) and redirection, I practiced how to:
* Audit system logs for failed authentication attempts.
* Secure critical system files like `/etc/shadow` to prevent unauthorized credential harvesting.
* Automate repetitive security tasks using Bash scripting to reduce human error.

## 💡 Lessons Learned
* **Permissions are Binary:** A single bit flipped in the permission string (e.g., `700` vs `777`) is the difference between a secure vault and a total data breach.
* **Data Hygiene:** Raw logs are "noise." Tools like `sort` and `uniq` are essential for converting massive datasets into actionable threat intelligence.
* **The Power of the Pipe:** Connecting simple tools (`ls | grep | wc`) allows for complex system queries that would be impossible to perform manually.

---

## 📂 Submission History
The following artifacts were validated and submitted via the Innovation Fellowship terminal:
* **Session 01:** `discovery.txt`
* **Session 02:** `harden.sh`
* **Session 03:** `threat_ips.txt`

---
*Developed as part of The Knowledge House Innovation Fellowship.*
