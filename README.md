# End-to-End Cyber Kill Chain Simulation & Detection using Wazuh SIEM

> Professional SOC lab simulating adversary activity, detection engineering, investigation, and incident response with Wazuh SIEM.

## Project Status

Baseline preparation is complete - lab health, Sysmon telemetry, and Wazuh ingestion are validated. Phase 1 is now live as a reconnaissance detection track with the first implemented Windows Firewall + Wazuh case study and expansion slots for Suricata and EDR perspectives.

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
| Project foundation | ✅ Completed | Repository standards, templates, and documentation controls are in place |
| Lab baseline | ✅ Completed | Agent health, network paths, Sysmon, and Wazuh ingestion are validated |
| Published attack scenarios | ✅ In Progress | Phase 1 reconnaissance is now structured as a three-variant detection track; Variant 01 documents Windows Firewall + Wazuh port-scan detection |
| Evidence handling | ✅ In Progress | Screenshots are stored with naming standards and SHA-256 inventory |

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

## Implemented Scenarios

- [`Phase 1 - Reconnaissance`](scenarios/01-reconnaissance/README.md)  
  Multi-telemetry reconnaissance track that begins with a Windows Firewall + Wazuh port-scan detection case study and expands toward Suricata and EDR-backed visibility.

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
