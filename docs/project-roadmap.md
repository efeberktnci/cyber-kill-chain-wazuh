# Project Roadmap

## Delivery Principles

- Establish telemetry and documentation baselines before attack simulation.
- Treat every scenario as a repeatable case study with the same evidence contract.
- Separate observed facts from analyst assessment.
- Publish only validated detections and sanitized evidence.
- Use small commits that represent one reviewable outcome.

## Phase 0 - Project Foundation

- Repository structure and Git conventions
- README landing page
- Architecture and network diagram specifications
- Scenario, evidence, screenshot, and incident-report templates
- Security and contribution guidance

**Exit criterion:** another analyst can understand how the project will be built and reviewed.

## Phase 1 - Lab and Telemetry Baseline

- Record VM roles, versions, and network addressing
- Document Wazuh components and agent enrollment
- Validate Windows Event Log and Sysmon generation
- Validate Sysmon ingestion, parsing, searchability, and timestamps in Wazuh
- Capture baseline health evidence

**Exit criterion:** telemetry can be traced from endpoint event to Wazuh record.

**Current state:** completed on the validated three-VM baseline documented in [`docs/lab-setup.md`](lab-setup.md) and [`docs/lab-baseline-evidence.md`](lab-baseline-evidence.md).

## Phases 2-9 - Scenario Case Studies

1. Reconnaissance
2. Execution
3. Credential Access
4. Persistence
5. Privilege Escalation
6. Defense Evasion
7. Discovery and Lateral Movement
8. Collection
9. Exfiltration

Each case passes the same lifecycle: plan, simulate, collect, detect, investigate, map, report, improve, review, and commit.

**Current state:** Scenario 01 is now implemented as a controlled Nmap-driven reconnaissance case study with Windows Firewall evidence and Wazuh port-scan correlation.

**Next planned scenario:** Execution with controlled Windows command and PowerShell activity mapped to endpoint telemetry and Wazuh alerting.

## Phase 10 - Final SOC Report

- Unified incident timeline
- Detection coverage matrix
- Cross-scenario findings and risk themes
- Executive and technical conclusions

## Phase 11 - Lessons Learned

- Visibility gaps
- False-positive and false-negative observations
- Detection backlog
- Lab and process improvements

## Phase 12 - Portfolio Expansion

Future work will be separated into focused repositories where scope warrants it: enterprise Active Directory, Kerberoasting, Pass-the-Hash, DCSync, Golden Ticket, Suricata, Sigma, SOAR, and threat intelligence with MISP/OpenCTI.
