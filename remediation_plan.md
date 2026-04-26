# CLOUDNANO REMEDIATION PLAN
**Operator:**Isabelli
 ## TOP 5 CRITICAL FIXES
*(From the 20 raw findings, select the 5 that pose the greatest ACTUAL risk. Explain your reasoning.)*

1. **Unauthenticated AWS S3 Bucket**
   * **Justification:** This poses an extreme risk of data exfiltration as sensitive business data is accessible to the public internet without any authentication.

2. **SQL Injection (SQLi) in Login Page**
   * **Justification:** This is a critical risk because it allows an attacker to bypass authentication entirely and gain full access to the backend database, potentially compromising all user accounts.

3. **Remote Code Execution (RCE) in Apache Struts**
   * **Justification:** This is the highest priority for server security, as it allows an attacker to take complete control of the web server and use it as a jumping-off point to attack the rest of the internal network. 

4. **SMBv1 Enabled**
   * **Justification:** Leaving this legacy protocol enabled creates a "wormable" environment where ransomware or malware can spread automatically across every computer on the internal network without user interaction.

5. **Cross-Site Scripting (XSS)**
   * **Justification:** This is a major threat to customers, as attackers can use it to hijack user sessions, steal login cookies, and perform unauthorized actions on behalf of legitimate users.
