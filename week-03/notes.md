# P1 · W3 · TLAB-03
# Phase 1 · Week 3 — Python Security Engineering, Scripting Automation, and Forensic Log Parsing

## Executive Summary
This week shifted focus from manual command-line execution to defensive automation using the Python programming language. Engineering tasks targeted network utility creation, structured error-handling architectures, process lifecycle auditing, and forensic string manipulation. Milestones achieved include compiling a multi-threaded network socket analyzer, developing a reliable authorization log parser capable of isolation without application failure, and generating machine-readable JSON security alerts during live active-defense hunting operations.

## Technical Implementation Analysis

### 1. Network Layer Socket Auditing
Using the native Python `socket` module, a low-level port-auditing tool (`port_check.py`) was engineered. 
* By establishing explicit internet protocol boundaries and iterating over complex address targets via looping logic patterns, the application manipulated state behaviors on TCP port 22 (Secure Shell). 
* Utilizing error code validation parameters (`connect_ex()`), network state behaviors were evaluated dynamically where a integer feedback evaluation of `0` verified an open door posture, while anything else signaled network layer filtering.

### 2. Defensive File I/O & Exception Isolation Architectures
To protect security monitoring applications against operational failure due to file deletion or log rotation dependencies, try-except blocks were introduced (`brute_detector.py`).
* Context managers (`with open()`) implemented reliable read-state lifecycles on active infrastructure records (`auth_audit.log`).
* Incorporating string matching rules (`"Failed password" in line`), a double-file conveyor platform read unparsed log blocks, filtered raw string values, dynamically appended text patterns directly into clean external data dumps (`brute_report.txt`), and tracks baseline metrics via incremental indicators.

### 3. Process Execution Monitoring and Forensic Response Serialization
Through integration with operating system kernel layers via the `subprocess` system interface, automated asset telemetry tools were developed (`system_auditor.py`).
* Execution hooks (`subprocess.run()`) invoked system states (`ps aux`), mapping string stdout configurations cleanly to memory streams via text-encoding normalization flags.
* In the final capstone exercise (`incident_response.py`), this platform was scaled into a full security automation script. The application parsed raw system metrics into lists via delimiter splitting parameters (`.split('\n')`), targeted target string arrays at static offsets (index `10`), and translated volatile string telemetry directly into an immutable, structured dictionary array. This state was safely written out into standard JavaScript Object Notation formats (`threat_report.json`) for automated API ingest.

## Industry Standard Alignment
Automating technical asset inventories and analyzing host process tables aligns heavily with Center for Internet Security (CIS) Control 9, which dictates the maintenance and protection of network infrastructure devices through active audit patterns (Center for Internet Security, 2021). Building custom software parsing models that convert raw unstructured string outputs into structured JSON file objects supports the automated ingestion standards demanded by modern Security Information and Event Management (SIEM) models as well as Security Orchestration, Automation, and Response (SOAR) technologies. Furthermore, building bulletproof script logic models that prevent application crashes via explicit Exception Isolation models implements system resilience objectives mandated by the National Institute of Standards and Technology (NIST) inside Special Publication 800-160 (NIST, 2018).

## References

Center for Internet Security. (2021). *CIS Controls Version 8: Security log management and analysis*. https://www.cisecurity.org/controls/v8/

National Institute of Standards and Technology. (2018). *Systems security engineering: Considerations for a multidisciplinary approach in the engineering of trustworthy secure systems* (NIST Special Publication 800-160, Vol. 1). U.S. Department of Commerce. https://doi.org/10.6028/NIST.SP.800-160v1
