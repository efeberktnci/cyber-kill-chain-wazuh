# Project Roadmap

## Delivery Principles

- Establish telemetry and documentation baselines before attack simulation.
- Treat every scenario as a repeatable case study with the same evidence contract.
- Separate observed facts from analyst assessment.
- Publish only validated detections and sanitized evidence.
- Use small commits that represent one reviewable outcome.

## Phase 0 — Project Foundation

- Repository structure and Git conventions
- README landing page
- Architecture and network diagram specifications
- Scenario, evidence, screenshot, and incident-report templates
- Security and contribution guidance

**Exit criterion:** another analyst can understand how the project will be built and reviewed.

## Phase 1 — Lab and Telemetry Baseline

- Record VM roles, versions, resources, and network addressing
- Document Wazuh components and agent enrollment
- Validate Windows Event Log and Sysmon generation
- Validate Sysmon ingestion, parsing, searchability, and timestamps in Wazuh
- Capture baseline health evidence

**Exit criterion:** telemetry can be traced from endpoint event to Wazuh record.

## Phases 2–9 — Scenario Case Studies

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

## Phase 10 — Final SOC Report

- Unified incident timeline
- Detection coverage matrix
- Cross-scenario findings and risk themes
- Executive and technical conclusions

## Phase 11 — Lessons Learned

- Visibility gaps
- False-positive and false-negative observations
- Detection backlog
- Lab and process improvements

## Phase 12 — Portfolio Expansion

Future work will be separated into focused repositories where scope warrants it: enterprise Active Directory, Kerberoasting, Pass-the-Hash, DCSync, Golden Ticket, Suricata, Sigma, SOAR, and threat intelligence with MISP/OpenCTI.

