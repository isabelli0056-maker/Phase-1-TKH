# P1 · W8 · TLAB-08
# Phase 1 · Week 8 — Advanced Exploitation, Privilege Escalation, and Tunnelling

## Executive Summary
This week shifted focus from defensive engineering to offensive penetration testing and post-exploitation mechanics. Operations validated how vulnerabilities are actively weaponized, how restricted system permissions are bypassed, and how compromised hosts are utilized to pivot into isolated network zones. 

## Technical Implementation Analysis

### 1. Remote Framework Exploitation
* **Mechanics:** Established manual reverse TCP connections using Netcat (`nc -lvnp`) to demonstrate outbound firewall bypassing.
* **Automation:** Utilized the Metasploit Framework (`msfconsole`) to exploit an unpatched Samba flaw (CVE-2007-2447). Delivering payloads to ports 139/445 automated command execution, yielding an unauthenticated administrative root shell (`exploit_verification.png`).

### 2. Privilege Escalation Frameworks
* **Sudo Binary Abuse:** Audited privilege tables (`sudo -l`) to identify a misconfigured binary tool (`/usr/bin/find`). Invoking specific sub-process execution flags (`-exec /bin/sh -p`) bypassed local user restrictions (`escalation_path.txt`).
* **Wildcard Cron Injection:** Exploited a root-owned automation task running a generic wildcard statement (`tar -cf backup.tar *`). Staging argument-wrapped filenames (`--checkpoint=1`) inside the execution directory forced the system to run a custom payload script, injecting SUID permissions onto a duplicate shell (`/tmp/rootbash -p`).

### 3. Multi-Tier Network Pivoting
* **Persistence:** Configured stable crontab backdoor paths to generate automated connection heartbeats.
* **Tunnelling:** Created a routing matrix through a compromised public web host (`172.60.0.10`) using Metasploit's `autoroute` module (`Deep_Pivot_Report.md`).
* **Pivoting:** Deployed a local SOCKS proxy tunnel. Passing scan commands through an encapsulation wrapper (`proxychains nmap -sT -Pn`) allowed successful enumeration of a hidden, air-gapped database enclave (`10.0.10.50`) without a direct physical link (`pivot_success.png`).

## Industry Standard Alignment
These offensive exercises directly support **Center for Internet Security (CIS) Control 5** (Account Management) and **Control 7** (Vulnerability Management) by demonstrating how configuration flaws alter enterprise risk profiles (Center for Internet Security, 2021). Simulating adversarial lateral movement patterns allows defensive engineers to evaluate and validate Zero Trust network isolation models as outlined in **NIST Special Publication 800-53** (NIST, 2020).

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Security log management and analysis*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
