# P1 · W6 · TLAB-06
# Phase 1 · Week 6 — Defensive Systems Architecture, Multi-Layer OSI Triage, and Infrastructure Hardening

## Executive Summary
This week marked the culmination of the core systems engineering curriculum through deep-dive diagnostic exercises, a formal technical practical examination, and a full-scale infrastructure deployment capstone (**Operation Hardened Outpost**). Core operational objectives focused on synthesizing host-level security configurations with network-layer access controls. Key milestones involved isolating conflicting socket assignments via advanced network monitoring utilities, constructing automated python environment watchdogs, executing filesystem data extraction routines under operational constraints, and authoring a comprehensive Security Architecture Document (SAD) to validate a hardened, multi-tier microservice environment.

## Technical Implementation Analysis

### 1. Multi-Layer OSI Troubleshooting and Socket Diagnostics
Operational validation tasks required auditing multi-layered system anomalies mimicking an active adversarial sabotage campaign across the Open Systems Interconnection (OSI) framework (`readiness_check.log`).
* **Layer 7 (Application):** Addressed permission delegation constraints by modifying discretionary access controls via symbolic notation (`chmod 755`), restoring execution pathways to critical diagnostic components.
* **Layer 4 (Transport):** Resolved port allocation conflicts preventing web server initialization. Utilizing socket statistics (`ss -tlnp`) filtered through string matching tools (`grep`), a rogue container tracking to port 8080 was discovered and administratively purged (`docker rm -f`). Connections were mapped from the host to container boundaries using raw netcat sweeps (`nc -zv`).
* **Layer 3 (Network):** Triage of outbound internet control message protocol (`ping`) failures identified localized packet filtering constraints. Interrogating the Uncomplicated Firewall platform (`ufw status numbered`) revealed explicit egress block rules, which were targeted and removed via rule index indicators.

### 2. Forensic Filesystem Mining & Exam Execution
During the technical evaluation phase (`practical_exam_report.txt`), multi-conditional search matrices were deployed to identify and extract privilege-restricted records across the system root structure.
* Standard error streams were redirected to zero-allocation block facilities (`2>/dev/null`) to optimize processing throughput.
* Targeted data clusters (`forge_alpha.log` and `forge_beta.log`) were successfully isolated via ownership and extension parameter filtering flags, moved into dedicated extraction staging boundaries under superuser execution states (`sudo`), and permanently locked down to a strict read-only posture (`chmod 444`) to enforce cryptographic immutability boundaries.

### 3. Comprehensive Infrastructure Hardening & Capstone Orchestration
The comprehensive capstone project (**The Hardened Outpost**) demanded the independent engineering of a resilient enterprise network node.
* **Perimeter Hardening:** The Secure Shell daemon configuration (`sshd_config`) was audited to explicitly enforce asymmetric cryptography authentication schemas while completely disabling standard password vectors and root login privileges. The network firewall was re-engineered to execute a default-deny posture, strictly whitelisting only essential service channels (ports 22 and 8080).
* **Automated Telemetry Watchdogs:** Automated python environment scripts (`dc_auditor.py`) were built to leverage core OS execution modules, conducting iterative accessibility validations against the enterprise Active Directory core domain and cataloging state updates within centralized logging paths (`/var/log/dc_audit.log`).
* **Air-Gapped Container Architecture:** A multi-tier microservice environment was defined using declarative orchestration scripts (`docker-compose.yml`), locking a production Nginx frontend inside a public-facing overlay network while completely embedding back-end database resources within an internal, air-gapped network layer with all host routing parameters completely cut off.

## Industry Standard Alignment
The engineering steps executed throughout this capstone align with Center for Internet Security (CIS) Control 4, which dictates the secure configuration of enterprise assets and software architectures through systematic port closing and credential locking (Center for Internet Security, 2021). Restricting SSH operational profiles to asymmetric key pairs while establishing a strict default-deny firewall boundary implements defense-in-depth principles outlined by the National Institute of Standards and Technology (NIST) within Special Publication 800-53 under the Identification and Authentication (IA) and System and Communications Protection (SC) families (NIST, 2020). Finally, consolidating the architectural state inside an immutable Security Architecture Document ensures alignment with formal industry compliance expectations and corporate configuration change-management tracks.

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Secure configuration of enterprise assets and software*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
