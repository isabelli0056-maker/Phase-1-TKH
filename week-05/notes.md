# P1 · W5 · TLAB-05
# Phase 1 · Week 5 — Identity & Access Management (IAM), Directory Services, and Cross-Platform Integration

## Executive Summary
This week evaluated the mechanics of enterprise directory architectures, programmatic account lifecycle management, and centralized policy enforcement across heterogeneous operating system environments. Engineering milestones involved deploying a Windows Server Active Directory Domain Services (AD DS) forest, writing automated identity provisioning scripts via object-oriented scripting platforms, and mapping Group Policy object templates to administrative boundaries. Additionally, an enterprise cross-platform bridging architecture was engineered, establishing a unified Pluggable Authentication Module (PAM) configuration that extends centralized Kerberos domain administrative permissions directly to localized Linux hosts.

## Technical Implementation Analysis

### 1. Automated Directory Provisioning & Identity Lifecycle Management
A Windows Server Core environment was promoted to a structural enterprise Root Domain Controller (`titan.local`) utilizing the Active Directory management engine via administrative scripting interfaces (`onboard_engineers.ps1`). 
* Scalable account provisioning was achieved by implementing programmatic iteration frameworks (`for` loops) linked directly to the `New-ADUser` provisioning model. 
* Organizational units (OUs) were structured (`OU=Engineering,DC=titan,DC=local`) to segment identities logically, ensuring that discretionary access rights, strict account control constraints (`-ChangePasswordAtLogon $true`), and global attribute values were programmatically applied uniformly across large workforce cohorts.



### 2. Centralized Group Policy Enforcement and Hierarchy Auditing
Administrative governance over the newly established domain workspace was achieved by engineering custom Group Policy Objects (GPOs) targeted at specific logical boundaries (`gpo_audit.txt`).
* A restrictive security configuration was built within the Group Policy Management Console (`Lockdown_ControlPanel`), modifying system registry keys via administrative templates to completely block localized host control console access.
* The application of policies was systematically validated across the Local, Site, Domain, and Organizational Unit (LSDOU) hierarchical framework. Policy sync engines (`gpupdate /force`) forced immediate client-side enforcement, validating that structural configurations inherit predictably down through container layers while preventing unapproved software installations by localized users.

### 3. Cross-Platform Directory Bridging & Unified Access Architecture
To eliminate identity isolation across multi-tenant infrastructures, an cross-platform identity system was deployed, linking an Ubuntu Linux VM directly to the Active Directory domain backend (`unified_identity.png`).
* Core network resolution dependencies were resolved by modifying the name resolution platform (`/etc/resolv.conf`) to target the primary domain nameserver. 
* System security discovery mechanics (`realmd` and `sssd`) bound the Linux operating system directly into the Kerberos realm. 
* By structuring individual configuration definitions (`sssd.conf`) and altering system privilege rules (`/etc/sudoers.d/domain_admins`), global domain security groups (`%domain\ admins`) were securely bridged to local superuser execution spaces. This layout allowed remote domain administrators to step into local administrative contexts, which was verified using credential switching validation commands (`su` and `whoami`).

## Industry Standard Alignment
Automating administrative account provisioning and strictly dividing domain structures into dedicated Organizational Units maps directly to Center for Internet Security (CIS) Control 6, which mandates the establishment and active management of access control credentials (Center for Internet Security, 2021). Furthermore, applying restrictive Group Policy objects to systematically lock down localized operating system configurations fulfills security compliance targets outlined by the National Institute of Standards and Technology (NIST) within Special Publication 800-53 under the Access Control (AC) and Configuration Management (CM) control families (NIST, 2020). Centralizing multi-platform validation metrics inside a unified Active Directory database satisfies modern Zero Trust security architecture baselines, minimizing the risk of localized account configuration drift and lateral credential harvesting.

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Access control management*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
