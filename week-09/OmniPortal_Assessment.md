# OMNI-PORTAL ASSESSMENT REPORT
**Operator:** Isabelli
 **Deadline:** April 5 @ 11:59 PM 

## PHASE 1: AUTH BYPASS (SQLi)
* **Payload Used:** ' OR 1=1 --
* **Result:** Successfully bypassed login and obtained 'auth_token' cookie.

## PHASE 2: CLIENT-SIDE HIJACK (XSS)
* **Stored XSS Payload:** <script>alert(document.cookie)</script>
* **Secret Cookie Captured:** auth_token=SUPPORT_TIER_1_SECRET_TOKEN

## PHASE 3: API ENUMERATION (BOLA)
* **Insecure Order ID:** 501
* **Confidential Data Leaked:** confidential server lease $15,000.00. 

## PHASE 4: THE REMEDIATION
* **Fix for SQLi:** Implement Parameterized Queries. This ensures that the database driver handles user input safely, preventing characters like ' or keywords like OR from being executed as commands. 
**Fix for XSS:** Apply Context-Aware Output Encoding. By converting special characters before they are rendered in the HTML, the browser treats them as literal text rather than executable scripts.
* **Fix for API BOLA:** Enforce Object-Level Authorization. The server must check that the user id associated with the auth token matches the owner of the order_id in the database before returning any data.
