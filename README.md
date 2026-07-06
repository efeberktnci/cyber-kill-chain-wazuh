# End-to-End Cyber Kill Chain Simulation & Detection using Wazuh SIEM

> Professional SOC lab simulating adversary activity, detection engineering, investigation, and incident response with Wazuh SIEM.

## Project Status

Phase 0 — Project foundation and documentation standards.

## Project Overview

This repository documents an end-to-end SOC workflow in an isolated virtual lab. Each scenario connects controlled attack simulation to endpoint telemetry, Wazuh detection, analyst investigation, MITRE ATT&CK and Cyber Kill Chain mapping, and a formal incident report.

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

Detailed infrastructure documentation will be maintained in [`docs/lab-setup.md`](docs/lab-setup.md).

## Architecture

Architecture and network diagrams are pending validated IP addressing and component versions.

- [`docs/architecture.md`](docs/architecture.md) — logical components and telemetry flow
- [`docs/network-design.md`](docs/network-design.md) — segmentation, addressing, and exposure rules

## Implemented Scenarios

No attack scenarios have been published. Reconnaissance will be the first case study after the lab baseline is validated.

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
