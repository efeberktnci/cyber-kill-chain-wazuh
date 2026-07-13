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

## Attack Phases 1-9 - Scenario Case Studies

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

**Current state:** Phase 1 is published as a completed primary reconnaissance case study using Windows Firewall evidence and Wazuh port-scan correlation. Additional Suricata + Wazuh and EDR + SIEM variants are intentionally deferred until the primary scenario from each remaining attack phase has been completed.

**Next planned scenario:** Execution with controlled Windows command and PowerShell activity mapped to endpoint telemetry and Wazuh alerting.

## Variant Strategy by Phase

| Phase | Variant Count | Why This Count Is Intentional |
|---|---:|---|
| 1. Reconnaissance | 3 | Host firewall, network IDS, and EDR/SIEM all provide meaningfully different visibility |
| 2. Execution | 3 | Command execution can be compared across Sysmon, PowerShell logging, and EDR telemetry |
| 3. Credential Access | 2 | Authentication evidence and host telemetry are the two strongest lenses without redundant repetition |
| 4. Persistence | 2 | Registry and scheduled task persistence create distinct but sufficient evidence paths |
| 5. Privilege Escalation | 1 | A single deep-dive case study is stronger than multiple shallow variants |
| 6. Defense Evasion | 2 | Obfuscation and security-control tampering are the two most valuable perspectives |
| 7. Discovery and Lateral Movement | 3 | Host discovery, remote access, and network movement deserve separate detection narratives |
| 8. Collection | 2 | Local staging and archive preparation provide enough analytical contrast |
| 9. Exfiltration | 3 | Egress behavior is best compared across host, network, and EDR/SIEM coverage |

## Publication Strategy

- First pass: complete one strong primary case study for every core attack phase
- Second pass: return to selected phases and publish the deferred comparison variants
- Completion status for a phase is tied to its published primary case study, not to every future comparison variant

## Phase 10 - Final SOC Report

- Unified incident timeline
- Detection coverage matrix
- Cross-scenario findings and risk themes
- Executive and technical conclusions

**Current state:** detection coverage is now being organized as phase-by-phase summary files under `detections/` instead of one oversized matrix, so GitHub preview stays readable as the project grows.

## Phase 11 - Lessons Learned

- Visibility gaps
- False-positive and false-negative observations
- Detection backlog
- Lab and process improvements

## Phase 12 - Portfolio Expansion

Future work will be separated into focused repositories where scope warrants it: enterprise Active Directory, Kerberoasting, Pass-the-Hash, DCSync, Golden Ticket, Suricata, Sigma, SOAR, and threat intelligence with MISP/OpenCTI.
