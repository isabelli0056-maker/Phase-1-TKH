# TITANCORP: PERIMETER ASSESSMENT REPORT
**Operator:** Isabelli
 **Target Subnet:** 172.88.0.0/24

## PHASE 1: ACTIVE ENUMERATION (NMAP)

* **Host 1 (172.88.0.1):** nginx 1.24.0 (Port 8080)
* **Host 2 (172.88.0.10):** nginx 1.14.2 (Port 80)
* **Host 3 (172.88.0.15):** Host up / no commom ports open

## PHASE 2: VULNERABILITY AUDIT (NIKTO)

* **Web Server 1 Finding:** X frame option header is missing.(Clickjacking vulnerability). 
* **Web Server 2 Finding:** outdated software version. 

## PHASE 3: RISK TRIAGE

* **Top Priority Remediation:** Outdated Web Server (Nginx 1.14.2) on 172.88.0.10.
* **Justification:** This poses the greatest risk because the Likelihood of exploitation is high due to public-facing known vulnerabilities (CVEs), and the Impact is critical as it could lead to full server compromise or unauthorized access to the DMZ.
