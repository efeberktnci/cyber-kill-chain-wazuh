# Phase 4 - Persistence

This phase will document how persistence mechanisms are established, what evidence they leave behind, and how that evidence is investigated.

## Persistence Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-registry-wazuh`](01-registry-wazuh/README.md) | :hourglass_flowing_sand: Planned | Registry telemetry + SIEM correlation | Persistence through registry modification investigated via endpoint and Wazuh evidence |
| [`02-scheduled-task-wazuh`](02-scheduled-task-wazuh/README.md) | :hourglass_flowing_sand: Planned | Scheduled task telemetry + SIEM correlation | Persistence through scheduled task creation and related telemetry investigated in Wazuh |

## Why This Phase Uses Two Variants

Registry persistence and scheduled task persistence are two of the clearest and most defensible lab scenarios. Together they provide enough contrast without making the phase bloated.
