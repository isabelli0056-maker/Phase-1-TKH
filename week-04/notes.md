# P1 · W4 · TLAB-04
# Phase 1 · Week 4 — Virtualization Engineering, Containerization, and Microservice Network Isolation

## Executive Summary
This week evaluated the security paradigms of hardware-level virtualization alongside OS-level virtualization (containerization). Operational exercises involved configuring host-only hardware boundaries to establish air-gapped malware detonation sandboxes, investigating Linux kernel namespace isolation constraints within container instances, and architecting multi-tier application environments via container orchestration platforms. Milestones achieved include compiling a secure deployment automation script and deploying an internal, network-segmented microservice cluster resilient against cross-zone pivot vectors.

## Technical Implementation Analysis

### 1. Hardware Hypervisor Isolation & Air-Gap Verification
A forensic sandbox ecosystem was engineered by manipulating the virtual network interface card (vNIC) state within a type-2 hypervisor framework (`sandbox_report.txt`). 
* Transitioning the hardware layout from a shared **Bridged Adapter orientation**—which exposes the asset directly to the broadcast domain of the physical local area network (LAN)—to a strict **Host-Only Adapter configuration** established an air-gapped security perimeter. 
* Network-layer egress validation tests via internet control message protocol (`ping`) confirmed total layer-3 external unreachability, validating that untrusted code structures detonated within the context layer cannot slip across internal subnets.



### 2. Namespace Isolation & Automated Container Deployments
Linux containerization mechanics were audited by provisioning localized operating system instances running atop an immutable micro-Linux engine (`deploy_web.sh`).
* Process namespace isolation was verified via runtime telemetry tools (`ps aux`), proving that processes executing inside the isolated application layer cannot enumerate the process identifiers (PIDs) running on the parent host operating system kernel.
* Port-forwarding boundaries were engineered to route localized socket traffic (`-p 8080:80`), exposing a highly transient, single-tier microservice environment that can be spun up, structurally modified via entry-point execution variables (`docker exec`), audited via standard output logs (`docker logs`), and instantly dismantled to enforce zero configuration drift.

### 3. Multi-Tier Microservice Orchestration and Network Segmentation
The final capstone exercise (**Operation Hyper-Stack**) required designing a declarative orchestration blueprint (`docker-compose.yml`) to govern a multi-tier WordPress web application and MariaDB back-end datastore cluster.
* Hardened network isolation was accomplished by explicitly declaring two isolated overlay networks: `public_net` (bridged to expose port 80 traffic externally) and `private_net` configured with internal routing parameters restricted (`internal: true`).
* The database engine was restricted exclusively to the `private_net` cluster, preventing external ingress attempts on port 3306 while preserving secure database communication with the application layer. Cross-zone isolation mapping tests verified that the internal container architecture had no reachable routing pathways to neighboring host-only networks, and system operational findings were cleanly serialized into structural reports (`hyperstack_audit.json`).

## Industry Standard Alignment
Isolating administrative testing assets inside host-only sandbox architectures aligns with the National Institute of Standards and Technology (NIST) Special Publication 800-53 control family for system flaws and protection configurations (NIST, 2020). Implementing distinct overlay network segments inside microservice infrastructures directly implements Center for Internet Security (CIS) Control 12, which mandates the architectural segmentation of enterprise networks to limit an adversary's lateral movement capabilities following initial perimeter compromise (Center for Internet Security, 2021). Furthermore, the orchestration of stateless containers using immutable infrastructure patterns adheres to modern DevSecOps standards, drastically minimizing host attack surface exposure over legacy monolithic systems.

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Network infrastructure management*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2020). *Security and privacy controls for information systems and organizations* (NIST Special Publication 800-53, Rev. 5). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-53r5
