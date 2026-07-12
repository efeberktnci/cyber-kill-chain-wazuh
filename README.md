# End-to-End Cyber Kill Chain Simulation & Detection using Wazuh SIEM

> Professional SOC lab simulating adversary activity, detection engineering, investigation, and incident response with Wazuh SIEM.

## Project Status

Baseline preparation is complete - lab health, Sysmon telemetry, and Wazuh ingestion are validated. The published Phase 1 reconnaissance case study is complete, while advanced comparison variants are intentionally deferred until the core phase sequence is fully implemented.

## Project Overview

This repository documents an end-to-end SOC workflow in an isolated virtual lab. Each scenario connects controlled attack simulation to endpoint telemetry, Wazuh detection, analyst investigation, MITRE ATT&CK and Cyber Kill Chain mapping, and a formal incident report.

## How to Navigate This Repository

If you are reviewing the project for the first time, use this reading order:

1. [`README.md`](README.md) for scope, status, and structure
2. [`docs/lab-setup.md`](docs/lab-setup.md) for the validated environment baseline
3. [`docs/lab-baseline-evidence.md`](docs/lab-baseline-evidence.md) for screenshot-backed proof of telemetry and ingestion
4. [`docs/architecture.md`](docs/architecture.md) and [`docs/network-design.md`](docs/network-design.md) for system and traffic context
5. [`docs/project-roadmap.md`](docs/project-roadmap.md) for the delivery sequence and upcoming case studies

## Current Snapshot

| Area | Status | Notes |
|---|---|---|
| Project foundation | :white_check_mark: Completed | Repository standards, templates, and documentation controls are in place |
| Lab baseline | :white_check_mark: Completed | Agent health, network paths, Sysmon, and Wazuh ingestion are validated |
| Published attack scenarios | :white_check_mark: Completed | Phase 1 reconnaissance is published as a completed primary case study, with advanced comparison variants deferred for later expansion |
| Evidence handling | :white_check_mark: Completed | Screenshots are stored with naming standards and SHA-256 inventory |

## Objectives

- Build a repeatable SOC investigation workflow.
- Develop and validate detection coverage using Windows, Sysmon, and Wazuh telemetry.
- Preserve defensible evidence and document analyst reasoning.
- Identify visibility gaps and convert lessons learned into detection improvements.

## Lab Environment

| Role | Platform | Purpose |
|---|---|---|
| Attacker | Kali Linux | Controlled attack simulation |
| Endpoint | Windows 10 | Monitored victim and Sysmon telemetry source |
| SIEM | Ubuntu / Wazuh | Collection, analysis, alerting, and investigation |

Detailed infrastructure documentation is maintained in [`docs/lab-setup.md`](docs/lab-setup.md). Baseline screenshots and integrity metadata are published in [`docs/lab-baseline-evidence.md`](docs/lab-baseline-evidence.md).

## Architecture

The core architecture and network model are now documented from the validated baseline.

- [`docs/architecture.md`](docs/architecture.md) - logical components and telemetry flow
- [`docs/network-design.md`](docs/network-design.md) - segmentation, addressing, and exposure rules

## Baseline Validation

Phase 1 established the minimum viable SOC telemetry chain for this repository:

- Windows 10 victim enrolled in Wazuh and reporting as an active agent
- Sysmon64 installed, auto-started, and running
- Endpoint-side Sysmon `Event ID 1` verified in Event Viewer
- Sysmon `Event ID 1` ingested and searchable in Wazuh Threat Hunting
- Kali-to-target and Kali-to-SIEM host-only connectivity validated
- Lab time alignment normalized across Kali, Windows, and Ubuntu

## Scenario Catalog

- [`Phase 1 - Reconnaissance`](scenarios/01-reconnaissance/README.md)  
  Completed primary case study using Windows Firewall + Wazuh port-scan detection. Suricata and EDR comparison variants are intentionally scheduled for post-core expansion.

- [`Phase 2 - Execution`](scenarios/02-execution/README.md)  
  Controlled command execution track planned across Sysmon, PowerShell, and EDR-oriented telemetry lenses.

- [`Phase 3 - Credential Access`](scenarios/03-credential-access/README.md)  
  Credential abuse track planned across authentication telemetry and host-level process visibility.

- [`Phase 4 - Persistence`](scenarios/04-persistence/README.md)  
  Persistence track planned around registry and scheduled task evidence paths.

- [`Phase 5 - Privilege Escalation`](scenarios/05-privilege-escalation/README.md)  
  Focused local privilege escalation case study planned as a single deep-dive variant.

- [`Phase 6 - Defense Evasion`](scenarios/06-defense-evasion/README.md)  
  Defense evasion track planned across obfuscated execution and endpoint protection tampering perspectives.

- [`Phase 7 - Discovery and Lateral Movement`](scenarios/07-discovery-lateral-movement/README.md)  
  Multi-variant host and remote movement track planned across endpoint and network visibility.

- [`Phase 8 - Collection`](scenarios/08-collection/README.md)  
  Collection track planned around local staging and archive preparation activity.

- [`Phase 9 - Exfiltration`](scenarios/09-exfiltration/README.md)  
  Multi-variant exfiltration track planned across egress, network IDS, and EDR/SIEM visibility.

## Repository Structure

```text
docs/          Project, architecture, lab, and operational documentation
diagrams/      Editable diagram sources and exported images
scenarios/     Self-contained attack-to-response case studies
detections/    Wazuh, Sysmon, and future detection content
reports/       Cross-scenario and final SOC reports
templates/     Controlled documentation and evidence templates
```

## Roadmap

See [`docs/project-roadmap.md`](docs/project-roadmap.md).

## Contributing and Security

See [`CONTRIBUTING.md`](CONTRIBUTING.md) for quality gates and [`SECURITY.md`](SECURITY.md) for safe disclosure and evidence-handling expectations.

## Responsible Use

All activity is intended for an isolated, authorized lab. Techniques and evidence must not include credentials, secrets, or data from systems outside the lab.

## License

Copyright is currently reserved. An explicit open-source license will be selected before the first public release; absence of a license does not grant reuse rights.
