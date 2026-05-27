# P1 · W1 · TLAB-01
# Phase 1 · Week 1 — Linux Engineering, Host Hardening, and Stream Editing

## Executive Summary
This week established foundational competencies in Linux systems administration, security posture baseline remediation, and automated log analysis. Key exercises involved navigating the Linux Filesystem Hierarchy Standard (FHS) to extract system telemetry, executing discretionary access control (DAC) modifications to secure critical identity assets, and constructing command-line pipelines to isolate Indicators of Compromise (IoCs) from live server logs.

## Technical Implementation Analysis

### 1. Filesystem Traversal and Environmental Auditing
Using specialized system tools, an environment audit was conducted across standard FHS pathways:
* **`/var/log`**: Evaluated system state retention and authentication logs (`syslog`, `auth.log`).
* **`/opt`**: Investigated localized, vendor-specific optional software configurations.
* **`/var/tmp`**: Audited volatile operational states to discover hidden directory structures and hidden security tokens via standard recursive flags (`ls -la`).

### 2. Discretionary Access Control (DAC) & Host Hardening
A severe system misconfiguration was audited wherein the critical authentication file `/etc/shadow` was exposed with world-writable and world-readable permissions (`777`). This state violates basic multi-tenant isolation principles. 
* Automated baseline corrections were established via a shell script (`harden.sh`).
* Permissions were restricted using `chmod 640` to ensure only privileged service groups can view password hashes.
* Ownership boundaries were reinforced using `chown root:shadow` to mitigate privilege escalation vectors.
* Secure Shell (`.ssh/`) user configurations were locked down to prevent unauthorized authentication persistence keys (`600` and `700` permissions respectively).



### 3. Stream Editing and Threat Intelligence Extraction
Faced with a live Structured Query Language (SQL) Injection attack signature (`UNION SELECT`), string matching utilities (`grep`) were combined with data-field extraction languages (`awk`) and sorting algorithms (`sort | uniq`) inside a POSIX pipeline. This automated parsing extracted distinct attacking IP addresses directly out of raw network transaction text blobs, generating an actionable blocklist file (`threat_ips.txt`).

## Industry Standard Alignment
According to the National Institute of Standards and Technology (NIST, 2020), securing system configurations requires strict enforcement of the Principle of Least Privilege. Allowing excessive file permissions on sensitive files like `/etc/shadow` leaves infrastructure highly vulnerable to local privilege escalation (LPE). Furthermore, automated log analysis aligns with the Center for Internet Security (CIS) Control 8, which mandates the collection, alerting, and retention of audit logs to effectively detect anomalous user behavior and active network incursions (Center for Internet Security, 2021).

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Audit log management*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
