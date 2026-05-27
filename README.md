# Phase 1 Cybersecurity Portfolio — Technical Infrastructure & Engineering Track

**Program:** TKH Innovation Fellowship 2026 | Phase 1 | Cybersecurity    

Welcome to my professional engineering portfolio. This repository serves as the centralized technical record of my engineering achievements, infrastructure deployments, and security assessments completed during Phase 1 of the fellowship. 

---

## 🛠️ Phase 1 Curriculum Architecture

This repository is organized into distinct weekly modules. Each folder contains functional source code, system configuration files, deployment manifests, and academic-grade analysis logs:

### 📂 [week-01/](./week-01/) — Linux Discovery & System Hardening
This initial module focused on mastering the Linux filesystem, automating access control, and performing stream-based log analysis for threat detection.
* **`discovery.txt`:** Mapping restricted system directories and extracting hidden telemetry.
* **`harden.sh`:** Automating permission sets (`chmod 700`/`600`) to enforce the Principle of Least Privilege.
* **`threat_ips.txt`:** Utilizing `grep`, `awk`, and `sed` to isolate malicious SQL Injection patterns from raw server logs.

### 📂 [week-02/](./week-02/) — Networking & Protocol Analysis
Focused on deep-packet inspection, OSI model layer troubleshooting, and protocol verification.
* **Artifacts:** Wireshark packet captures (`.pcap`), transport layer connection matrices, and frame decoding logs mapping rogue network traffic.

### 📂 [week-03/](./week-03/) — Python Scripting for Security
Automating system auditing and network defense mechanisms using programmatic scripts.
* **Artifacts:** Custom multi-threaded port scanners, regex-based log parsers, and cryptographic hash verification tools.

### 📂 [week-04/](./week-04/) — Virtualization & Containers
Isolating enterprise service architectures using lightweight container runtimes.
* **Artifacts:** Multi-stage production `Dockerfiles`, network-isolated `docker-compose.yml` stacks, and container resource constraints.

### 📂 [week-05/](./week-05/) — Identity, Access & Active Directory
Managing centralized identity infrastructures and group policies under restricted access models.
* **Artifacts:** Active Directory domain trees, Group Policy Objects (GPOs), and administrative access profiles mapped out within headless **Windows Server Core** deployments.

### 📂 [week-06/](./week-06/) — Phase 1 Midterm Blueprint
Designing and documenting an enterprise security posture framework.
* **Artifacts:** `HardenedOutpost_SAD.pdf` System Architecture Document outlining secure perimeter zoning, physical controls, and defensive topologies.

### 📂 [week-07/](./week-07/) — Reconnaissance & Vulnerability Analysis
Executing passive OSINT discovery and active target vulnerability profiling.
* **Artifacts:** `ThreatProfile_CloudNano.md`, `nmap_scan_results.txt`, `remediation_plan.md`, and the overall master `Perimeter_Assessment.md`.

### 📂 [week-08/](./week-08/) — Advanced Exploitation Frameworks
Simulating adversarial lateral movement, privilege escalation, and internal network pivots.
* **Artifacts:** Metasploit automation captures (`exploit_verification.png`), local SUID binary exploitation tracks (`escalation_path.txt`), and internal SOCKS proxy tunnels (`Deep_Pivot_Report.md`).

### 📂 [week-09/](./week-09/) — Web Application Security (OWASP Top 10)
Identifying, exploiting, and remediating high-impact vulnerabilities within web services and REST APIs.
* **Artifacts:** SQL Injection authentication bypass files, Stored XSS cookie hijacking scripts, Burp Suite API interception logs, and the unified `OmniPortal_Assessment.md` report.

### 📂 [week-10/](./week-10/) — Digital Forensics & Incident Response (DFIR)
Executing host machine containment, cryptographic preservation, and forensic memory/disk carving.
* **Artifacts:** Volatile evidence preservation chains (`collection_log.txt`), Sleuth Kit inode file carving files (`forensic_findings.md`), ELK SIEM log correlation patterns (`attack_timeline.csv`), and the unified `Incident_Response_Report.md`.

### 📂 [week-11/](./week-11/) — Active Defense & Defense-in-Depth
Engineering layered, proactive controls across network perimeters and local endpoints.
* **Artifacts:** Demilitarized Zone routing rules (`firewall_config.sh`), custom Suricata intrusion signatures (`custom_ids.rules`), Sysmon ransomware detection policies (`edr_policy.xml`), and the master blueprint framework (`Operation_Fortress_Report.md`).

### 📂 [week-12/](./week-12/) — Professional Portfolio Audit
Formal self-assessment logging and phase closure verification.
* **Artifacts:** `portfolio_audit.md` documenting repository visibility verification, completeness matrices, and comprehensive professional reflections.

---

## 🧠 Core Technical Competencies Demonstrated
* **Defensive Engineering:** Kernel-level packet filtering (`iptables`), IDS Signature Writing (`Suricata`), EDR Policy Management (`Sysmon for Linux`), SIEM Log Aggregation (`ELK Stack`).
* **Systems Administration:** Advanced Linux Shell Automation (Bash), Python Scripting, Container Optimization (Docker), Identity Management (Active Directory / GPO / Windows Server Core).
* **Security Assessments:** Web Application Auditing (Burp Suite), Threat Identification (Nmap, Metasploit), Host & Disk Forensics (The Sleuth Kit).

---

## 📋 Professional Framework Alignment
All administrative logs, configuration scripts, and technical reflections are documented using **APA formatting** constraints. The defensive systems engineering practices implemented throughout this repository align explicitly with global security control requirements under **Center for Internet Security (CIS) Controls v8** and **NIST Special Publication 800-53**.
