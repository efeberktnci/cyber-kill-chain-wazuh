# Phase 3 - Credential Access

This phase will document controlled credential access activity and the defender evidence it creates on the endpoint and in the monitoring stack.

## Credential Access Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-windows-auth-wazuh`](01-windows-auth-wazuh/README.md) | :hourglass_flowing_sand: Planned | Windows authentication telemetry + SIEM correlation | Authentication failures and credential abuse indicators investigated through Windows and Wazuh evidence |
| [`02-sysmon-wazuh`](02-sysmon-wazuh/README.md) | :hourglass_flowing_sand: Planned | Host process telemetry + SIEM correlation | Credential tooling or suspicious host behavior investigated through Sysmon and Wazuh |

## Why This Phase Uses Two Variants

For credential access, the strongest contrast usually comes from authentication evidence versus host-level execution evidence. A third lens often becomes repetitive unless the lab expands into domain services or dedicated network authentication telemetry.
