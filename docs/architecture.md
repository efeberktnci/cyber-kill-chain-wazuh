# SOC Lab Architecture

## Purpose

The architecture supports controlled adversary simulation, endpoint telemetry collection, centralized detection, and reproducible investigation without exposing the lab to production systems.

## Logical Components

| Component | Responsibility | Trust Boundary |
|---|---|---|
| Kali Linux | Generates authorized test activity | Adversary simulation zone |
| Windows 10 victim | Produces native and Sysmon telemetry | Monitored endpoint zone |
| Wazuh Agent | Collects configured endpoint events | Endpoint-to-SIEM boundary |
| Wazuh Manager | Decodes events and evaluates rules | Detection processing zone |
| Wazuh Indexer | Stores and indexes security events | Security data zone |
| Wazuh Dashboard | Supports alert review and investigation | Analyst access zone |

## Telemetry Flow

```text
Kali Linux
    | authorized simulation
    v
Windows 10 victim
    | Windows Event Log + Sysmon
    v
Wazuh Agent
    | encrypted agent communication
    v
Wazuh Manager -> Wazuh Indexer -> Wazuh Dashboard
                                      |
                                      v
                               Analyst investigation
```

## Architecture Decisions

- Sysmon is part of the baseline, not a later enhancement.
- Endpoint generation and SIEM ingestion are tested independently.
- Raw evidence is excluded from Git when it may contain sensitive or high-volume data.
- Scenario documentation records the exact telemetry and detection dependencies.

## Validation Status

Phase 1 validation is complete:

- Endpoint-side Sysmon generation is verified
- Wazuh agent enrollment is active
- Sysmon `Event ID 1` is decoded, indexed, and searchable in Wazuh
- Dashboard-side document inspection confirms parsed Sysmon fields
- Lab time alignment has been normalized for scenario work
