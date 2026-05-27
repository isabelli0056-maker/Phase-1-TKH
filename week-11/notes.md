# Phase 1 · Week 11 — Defensive Systems Engineering, Active Detection, and Defense-in-Depth Architecture

## Executive Summary
This week focused on engineering and implementing an integrated, multi-layered defensive security posture across network boundaries and host endpoints. Operational milestones included managing structural Demilitarized Zone (DMZ) traffic filtering, authoring signature verification patterns for network Intrusion Detection Systems (IDS), and configuring Endpoint Detection and Response (EDR) policy logs to capture ransomware execution states. Exercises culminated in **Operation Fortress**, which demonstrated how independent technological controls act as structural backups for one another to block, flag, and stop threat actors.

## Technical Implementation Analysis

### 1. DMZ Boundary Control & Net Filtering
* **Posture Enforcement:** Managed host-level profiles via the Uncomplicated Firewall (`ufw`) engine to configure a default-deny posture, explicitly whitelisting only essential service channels (ports 22 and 443).
* **Lateral Movement Prevention:** Engineered strict state rules using kernel-level packet inspection tables (`iptables`). Allowed inbound connections to open web instances while blocking outward scanning to adjacent subnets (`-A OUTPUT -d 10.0.5.0/24 -j DROP`), reserving explicit egress allowances exclusively for database transactions on port 3306 (`firewall_config.sh`).

### 2. Perimeter Traffic Inspection (IDS Signatures)
* **Protocol Trapping:** Authored custom snort-format rules within Suricata monitoring environments to identify network scanning trends (`custom_ids.rules`).
* **Application Header Mining:** Developed targeted inspection profiles matching malicious application-layer identifiers, checking specific TCP packet content blocks for malicious user-agent strings (`content:"Ghost_Scanner_v1"`) or web shell exploitation commands (`cmd=whoami`) crossing the network bridge.

### 3. Host Monitoring & EDR Configuration
* **Process Telemetry Logging:** Initialized System Monitor for Linux (`Sysmon`) to record underlying process behavior, tracking parent-child process chains via Event ID 1.
* **Precursor Behavior Catching:** Engineered targeted XML policy filters (`edr_policy.xml`) designed to alert on known ransomware activities, specifically looking for Volume Shadow Copy manipulation attempts (`delete shadows`).
* **Full-Chain Blueprint Integration:** Orchestrated firewall rules, IDS signatures, and EDR policies together during **Operation Fortress** (`Operation_Fortress_Report.md`) to establish an integrated defense-in-depth model that protects assets across three independent infrastructure layers.



## Industry Standard Alignment
Building and deploying multi-tier detection matrices matches requirements within **Center for Internet Security (CIS) Control 12** (Network Infrastructure Management) and **Control 13** (Network Monitoring and Defense), which demand continuous monitoring and strict traffic containment (Center for Internet Security, 2021). Furthermore, applying layered detection mechanisms ensures alignment with formal information protection parameters established under the System and Communications Protection (SC) and System and Information Integrity (SI) control families of **NIST Special Publication 800-53** (NIST, 2020).

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Network monitoring and defense*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5# P1 · W11 · TLAB-11
