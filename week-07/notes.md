# P1 · W7 · TLAB-07
# Phase 1 · Week 7 — Defensive Reconnaissance, Network Mapping, and Vulnerability Assessment

## Executive Summary
This week simulated a comprehensive security assessment framework replicating an acquisition auditing track for an incoming external entity ("CloudNano"). Operations evaluated both non-intrusive Open-Source Intelligence (OSINT) methodologies and intrusive packet manipulation tactics to map external attack surfaces. Operational milestones included tracking metadata leaks via search engine index shodan platforms, building targeted network-layer scan vectors using raw sockets, auditing localized transport interfaces for missing configurations, and executing strategic triage frameworks that prioritize actual threat models over generic vulnerability score metrics.

## Technical Implementation Analysis

### 1. Passive Cyber Reconnaissance & Exposure Profiling
To model early-stage adversarial discovery vectors without triggering target security operations center alert monitors, non-intrusive OSINT profiles were constructed (`ThreatProfile_CloudNano.md`).
* Public banner evaluation was executed via the Shodan platform to extract leaked target configuration data, exposed remote administration endpoints (RDP on port 3389), and unpatched protocol utilities (vsFTPd 2.3.4).
* Open-source domain mining engines (`sublist3r`) scraped public records to enumerate DNS subdomain hierarchies. Corporate identity exposure vectors were cross-referenced against public compromise repositories (`HaveIBeenPwned`) alongside platform footprint analyzers (`BuiltWith`) to map external web platforms and trace identity leaks across third-party environments.

### 2. Active Network Mapping and Service Interrogation
Intrusive footprint mapping was executed inside isolated network environments using raw socket manipulation engines (`nmap_scan_results.txt`).
* Initial asset identification used network layer echo requests (`-sn` ping sweeps) across an allocated classless address space (`172.99.0.0/24` and `172.88.0.0/24`) to isolate live host environments.
* Identified network targets were subjected to intense transport layer interrogation, including aggressive version detection scans (`-sV`) and complete socket index audits (`-p-` 1-65535). This process parsed application headers to map outdated software releases and discover hidden operational access panels.



### 3. Web Application Auditing and Context-Driven Risk Triage
Active vulnerability analysis was conducted against local staging targets using dedicated application web parsing frameworks (`remediation_plan.md` and `Perimeter_Assessment.md`).
* Web platform scans (`nikto`) systematically mapped target software arrays, discovering active web paths, missing transport configurations (such as missing `X-Frame-Options` blocks), and exploitable data structures.
* The raw output was evaluated using an advanced engineering risk prioritization framework rather than relying strictly on Common Vulnerability Scoring System (CVSS) base metrics. Using the standardized risk evaluation equation:
$$\text{Risk} = \text{Likelihood} \times \text{Impact}$$
vulnerabilities were triaged based on context, asset exposure values, and data sensitivity. This strategy ensured that remediation pipelines targeted accessible production risks—like public S3 buckets leaking customer data—ahead of theoretically high-severity items trapped within air-gapped system segments.

## Industry Standard Alignment
Conducting passive footprinting alongside systematic active vulnerability identification directly satisfies Center for Internet Security (CIS) Control 7, which dictates continuous vulnerability management to minimize enterprise attack surfaces (Center for Internet Security, 2021). Programmatically mapping and analyzing asset states matches requirements within the National Institute of Standards and Technology (NIST) Special Publication 800-53 under the Risk Assessment (RA) and System and Information Integrity (SI) control branches (NIST, 2020). Furthermore, applying business-context prioritization to discovered security issues satisfies industry standards for effective risk treatment, focusing remediation capital where it delivers the highest return on security investment.

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Continuous vulnerability management*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
