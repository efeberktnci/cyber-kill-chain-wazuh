# Phase 2 - Execution

This phase will document controlled command execution from attacker action through endpoint telemetry, SIEM detection, and analyst investigation.

## Execution Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-sysmon-wazuh`](01-sysmon-wazuh/README.md) | :hourglass_flowing_sand: Planned | Sysmon process telemetry + SIEM correlation | Command execution visibility through process creation, parent-child relationships, and Wazuh alerting |
| [`02-powershell-wazuh`](02-powershell-wazuh/README.md) | :hourglass_flowing_sand: Planned | PowerShell logging + SIEM correlation | PowerShell-focused execution detection using script block or operational logging |
| [`03-edr-siem`](03-edr-siem/README.md) | :hourglass_flowing_sand: Planned | Endpoint detection + SIEM perspective | Endpoint execution telemetry and detection context compared against SIEM findings |

## Why This Phase Uses Three Variants

Execution is one of the strongest phases for telemetry comparison. The same command can look different in Sysmon, PowerShell-specific logging, and EDR/SIEM workflows, so a three-variant structure adds real analytical value instead of repetition.
