# P1 · W10 · TLAB-10
# Phase 1 · Week 10 — Digital Forensics and Incident Response (DFIR)

## Executive Summary
This week evaluated systemic methodologies for tracking, identifying, and mitigating active threat behaviors within enterprise systems. Operations simulated the complete lifecycle of a high-impact network breach, moving from real-time host isolation to dark file system extraction and log telemetry analytics. Key milestones included establishing cryptographically secure data evidence paths, restoring deleted malware execution files from raw disk blocks using localized file carving engines, and constructing comprehensive attack timelines via Security Information and Event Management (SIEM) systems.

## Technical Implementation Analysis

### 1. Live System Triage and Evidence Integrity
* **Volatile Data Gathering:** Accessed a compromised live container environment (`compromised_host`) to trace network connection metadata. Utilizing native socket auditing utilities (`netstat -antp`), an rogue Command and Control (C2) beacon process executing over port 4444 was isolated (`collection_log.txt`).
* **Cryptographic Preservation:** Created immutable digital fingerprints of gathered system media (`memory_dump.raw` and `system_artifacts.zip`) by calculating explicit `md5sum` and `sha256sum` hashes, satisfying core Chain of Custody compliance regulations for forensic artifacts.

### 2. File Carving and Memory Post-Mortem
* **RAM String Harvesting:** Carved raw system memory strings (`memdump.raw`) to bypass standard kernel visibility layers and isolate hidden malicious background configurations.
* **Disk Data Recovery:** Utilized The Sleuth Kit toolkit (`fls -r`) to parse raw metadata structures within a disk dump (`compromised_drive.dd`). Deleted malware entities (`Resume.exe`/`beacon.exe`) were located via active Master File Table (MFT) index pointers. Applying data recovery utilities (`icat`) targeted at the explicit block inode indexes bypassed operating system restrictions to successfully pull out hidden malware instruction strings (`forensic_findings.md`).

### 3. Distributed Log Correlation and Threat Timeline Analysis
* **SIEM Index Creation:** Provisioned an enterprise Elasticsearch-Logstash-Kibana (ELK) deployment, establishing dynamic indices (`enterprise_logs*`) to centralize log telemetry events.
* **Timeline Reconstruction:** Queried security audit sources to map unauthorized authentication behaviors and correlate threat operations across the network topology (`attack_timeline.csv`). Cross-referencing web traffic logs, active directory changes, and outbound firewall records by shared IP indicators and timestamps exposed the explicit lateral movement pathways and data theft volumes used during the breach.
* **Incident Lifecycle Compilation:** Synthesized triage findings, cryptographic file proofing, disk data mining, and SIEM logging intelligence into a master corporate review file (**Operation Phantom Pursuit**), generating an industry-ready post-incident summary (`Incident_Response_Report.md`).

## Industry Standard Alignment
The technical steps completed throughout this DFIR track map directly to **Center for Internet Security (CIS) Control 17** (Incident Response Management), which dictates the execution of formal procedures to ensure rapid threat identification and data protection (Center for Internet Security, 2021). Preserving data integrity through precise hashing routines and conducting thorough analysis of log records fulfills incident response and data preservation baselines defined within **NIST Special Publication 800-53** under the Incident Response (IR) and Audit and Accountability (AU) control frameworks (NIST, 2020).

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Incident response management*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
