# Lab Setup

## Status

Phase 1 is complete. The lab baseline has been validated from endpoint event generation through Wazuh ingestion and dashboard searchability.

## Lab Summary

This project runs in an isolated VirtualBox lab with three primary systems:

| Asset | Role | Operating System | Network Role | Telemetry Role | Status |
|---|---|---|---|---|---|
| Kali VM | Attacker | Kali GNU/Linux 2026.2 | Attack simulation host | None | Running |
| Windows victim | Endpoint | Microsoft Windows 10 Pro | Monitored target | Wazuh Agent, Sysmon | Running |
| Wazuh server | SIEM | Ubuntu 24.04.4 LTS | Manager, indexer, dashboard host | Wazuh Manager, Indexer, Dashboard | Running |

## Network Configuration

The lab uses two VirtualBox networks per VM:

- `Adapter 1`: NAT for Internet access, package installation, and feed updates.
- `Adapter 2`: Host-only network for controlled east-west lab traffic.

### Addressing

| Asset | NAT Interface | NAT Address | Host-only Interface | Host-only Address | Default Route |
|---|---|---|---|---|---|
| Kali VM | `eth0` | `10.0.2.15/24` | `eth1` | `192.168.56.10/24` | `10.0.2.2` via `eth0` |
| Windows victim | Adapter 1 | `10.0.2.15/24` | Adapter 2 | `192.168.56.103/24` | NAT-backed |
| Wazuh server | `enp0s3` | `10.0.2.15/24` | `enp0s8` | `192.168.56.105/24` | `10.0.2.2` via `enp0s3` |

> Note: repeated `10.0.2.15` addresses are expected in VirtualBox NAT mode because each guest uses an isolated NAT segment.

## Time and Regional Settings

Time alignment was normalized across the lab before attack simulation.

| Asset | Time Zone | Sync Status |
|---|---|---|
| Kali VM | `Europe/Istanbul` | NTP active and synchronized |
| Windows victim | `(UTC+03:00) Istanbul` | Local time aligned with lab |
| Wazuh server | `Europe/Istanbul` | NTP active and synchronized |

## Wazuh Platform Validation

The SIEM node is operating as a single-node Wazuh deployment:

- `wazuh-manager`: active
- `wazuh-indexer`: active
- `wazuh-dashboard`: active
- Wazuh control components required for this phase were confirmed running

The enrolled endpoint validated in this phase is:

| Field | Value |
|---|---|
| Agent ID | `001` |
| Agent name | `DESKTOP-43MPG6R` |
| Agent version | `v4.14.6` |
| Group | `default` |
| Status | `active` |

## Sysmon Validation

Sysmon was added to the Windows victim as a baseline telemetry source and validated in two stages:

1. Endpoint generation
   Verified in `Microsoft-Windows-Sysmon/Operational`.
2. Wazuh ingestion
   Verified in Wazuh Threat Hunting with parsed document fields.

Observed event coverage during baseline validation included:

- `Event ID 1`: Process Create
- `Event ID 11`: File Create
- `Event ID 22`: DNS Query

Service-level validation confirmed:

- Service name: `Sysmon64`
- Start type: `AUTO_START`
- Binary path: `C:\Windows\Sysmon64.exe`
- Runtime state: `Running`

## Baseline Validation Outcome

Phase 1 exit criteria were met:

- Windows endpoint telemetry is generated locally.
- Sysmon service health is confirmed.
- Wazuh agent enrollment is active.
- Sysmon `Event ID 1` is searchable in Wazuh.
- Time configuration is aligned well enough for scenario work.

## Evidence Pack

The sanitized baseline evidence set is stored in [`docs/lab-baseline-evidence.md`](lab-baseline-evidence.md) and the corresponding screenshots under `docs/assets/screenshots/lab-baseline/`.
