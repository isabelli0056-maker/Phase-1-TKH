# P1 · W2 · TLAB-02
# Phase 1 · Week 2 — OSI Model Triage, Subnet Engineering, and Protocol Interrogation

## Executive Summary
This week involved an intensive investigation into multi-layer network disruptions, simulating an adversarial sabotage scenario across the Open Systems Interconnection (OSI) model. Operational tasks required systematic engineering triage from the Physical and Data Link layers up to the Application layer. Core objectives included physical link restoration, logical boundary recalculation via variable-length subnet masks (VLSM), local DNS cache poisoning remediation, and the collection of cryptographic/forensic packet telemetry proving connection recovery.

## Technical Implementation Analysis

### 1. Physical and Data Link Layer Recovery (Layers 1–2)
A deliberate interface shutdown was investigated using the `ip link` utility. By issuing administrative overrides (`ip link set up`), the link-state of the primary virtual network interface card (vNIC) was forced into an operational orientation. This step resolved default gateway unreachable errors and allowed hardware frame exchanges to resume.

### 2. Subnet Remediation & Border Gateway Routing (Layer 3)
Adversarial configuration tampering isolated the host by applying an invalid `/26` subnet mask (`10.50.50.150/26` / `192.168.10.x/26`). Through binary interrogation using python algorithms (`bin()`) and network calculations via `ipcalc`, it was demonstrated that a `/26` architecture split the local topology, placing the default gateway outside the accessible host min/max range.
* The restriction was bypassed by altering the interface boundaries to a classless `/24` mask.
* The logical routing platform was stabilized by manually re-injecting the static gateway entry into the kernel routing table (`ip route add default via`).



### 3. DNS Cache Poisoning & Protocol Verification (Layers 4 & 7)
The local domain lookup mechanism was audited to reveal local loopback redirects inside `/etc/hosts`, mapping legitimate web environments to internal socket layers (`127.0.0.1` and `10.99.99.99`). 
* Unauthorized string records were parsed and purged using administrative text manipulation.
* Domain Information Groper (`dig`) lookups validated the resumption of trusted exterior nameserver handshakes.
* To finalize forensic proof of operation, side-by-side terminal instances coupled a resource browser (`curl`) with a low-level packet capture engine (`tcpdump`). Telemetry successfully isolated the exact chronological sequencing of the transmission control protocol (TCP) three-way handshake, identifying the Synchronize (`[S]`), Synchronize-Acknowledgment (`[S.]`), and Final Acknowledgment (`[.]`) flag parameters.

## Industry Standard Alignment
According to the Internet Engineering Task Force (IETF, 1981), a rigorous validation of the TCP 3-way handshake provides undeniable forensic verification that bi-directional, stateful layer-4 sessions can be reliably established. Mitigating the local name redirection preserves internal data pathways against unauthorized man-in-the-middle (MitM) positioning as mapped out in the MITRE ATT&CK framework under sub-technique T1557 (MITRE ATT&CK, 2020). Correcting these flawed subnet boundaries matches the foundational controls within the National Institute of Standards and Technology (NIST) Special Publication 800-160, ensuring system modularity and predictable boundary isolation constraints (NIST, 2018).

## References

Internet Engineering Task Force. (1981). *Transmission Control Protocol* (RFC 793). Information Sciences Institute. https://datatracker.ietf.org/doc/html/rfc793

MITRE ATT&CK. (2020). *Adversary tactics, techniques & common knowledge: Adversary-in-the-middle* (Technique T1557). https://attack.mitre.org/techniques/T1557/

National Institute of Standards and Technology. (2018). *Systems security engineering: Considerations for a multidisciplinary approach in the engineering of trustworthy secure systems* (NIST Special Publication 800-160, Vol. 1). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-160v1
