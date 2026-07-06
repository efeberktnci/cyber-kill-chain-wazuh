# Lab Setup

## Status

Inventory collection and Wazuh ingestion validation are in progress.

## Components

| Asset | Role | Operating System | Address | Telemetry | Status |
|---|---|---|---|---|---|
| Kali VM | Attacker | Kali Linux | TBD | N/A | Running |
| Windows VM | Victim endpoint | Windows 10 | TBD | Wazuh Agent, Sysmon | Sysmon generation verified |
| Wazuh VM | SIEM | Ubuntu | TBD | Wazuh Manager, Indexer, Dashboard | Running |

## Sysmon Validation

Endpoint-side generation was visually verified on 2026-07-06 in `Microsoft-Windows-Sysmon/Operational`. Observed event IDs included:

- 1 — Process Create
- 11 — File Create
- 22 — DNS Query

Wazuh-side ingestion and searchability remain pending and must be validated before the first scenario.

## Information Required

- Exact operating-system and Wazuh versions
- Static or current IP addresses and network mode
- VM resource allocations
- Wazuh agent identifier and connection status
- Sysmon version and configuration source/hash
- Time synchronization and timezone configuration

