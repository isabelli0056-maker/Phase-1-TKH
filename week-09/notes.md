# P1 · W9 · TLAB-09
# Phase 1 · Week 9 — Web Application Security, API Penetration Testing, and OWASP Top 10

## Executive Summary
This week evaluated foundational vulnerabilities inside modern web applications and RESTful API structures mapping to the OWASP Top 10 framework. Operational milestones included executing data exfiltration strategies via injection matrices, mapping flaws in browser cookie handling, and manipulating API parameters using proxy interception frameworks to bypass business logic controls. Exercises culminated in **Operation Omni-Portal**, which required chaining multi-vector attacks in sequence to compromise an enterprise system.

## Technical Implementation Analysis

### 1. SQL Injection (SQLi) & Data Exfiltration
* **Authentication Bypass:** Injected a classic SQL tautology (`' OR 1=1 --`) to manipulate boolean login query logic, bypassing authentication gateways without valid user credentials (`sqli_report.txt`).
* **UNION-Based Extraction:** Enumerated application layout constraints via `ORDER BY` syntax to determine column boundaries. Executed a `UNION SELECT` attack against SQLite internal metadata storage (`sqlite_master`) to map the structural backend schema and exfiltrate sensitive payroll records from the underlying target database.

### 2. Client-Side Browser Exploitation (XSS & CSRF)
* **Reflected & Stored XSS:** Injected arbitrary JavaScript (`<script>alert(document.cookie)</script>`) into unsanitized user fields (`xss_payloads.txt`). Validated Document Object Model (DOM) control and permanently poisoned interactive message forums to steal session identities (`auth_token`).
* **Cross-Site Request Forgery (CSRF):** Exploited the absence of cryptographic anti-CSRF verification tokens by weaponizing transaction-routing links within standard HTML image tags (`<img src="...">`), forcing unapproved state changes on authenticated users.

### 3. API Security & Broken Object Level Authorization (BOLA)
* **Parameter Manipulation:** Utilized Burp Suite Proxy to intercept live REST API endpoints (`/api/v1/profile/101`), changing object identification variables to expose unlinked administrative files (`api_audit.log`).
* **Automated Intruder Sweeps:** Managed automated payload arrays via Burp Intruder to brute-force numeric business logic inputs, exposing private checkout discount values.
* **Full-Chain Capstone Integration:** Integrated SQLi, Stored XSS, and API BOLA patterns concurrently against the unified Omni-Portal application (`OmniPortal_Assessment.md`), completing full systemic compromise and extracting protected corporate orders.

[Image mapping full-chain web exploitation flow from initial SQLi login bypass to API BOLA exfiltration]

## Industry Standard Alignment
Auditing web applications against top structural flaws directly supports **Center for Internet Security (CIS) Control 16** (Application Software Security), which mandates steady vulnerability mitigation throughout software deployment processes (Center for Internet Security, 2021). Correcting injection flaws via parameterized queries and handling input sanitization implements developer standards highlighted within **NIST Special Publication 800-53** under the System and Information Integrity (SI) control class (NIST, 2020).

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Application software security*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
