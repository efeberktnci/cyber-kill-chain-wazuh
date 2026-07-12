# Scenario Case Studies

Each numbered directory is a self-contained case study that follows the same analyst workflow:

1. Objective and lab scope
2. Controlled attack simulation
3. Endpoint and Wazuh evidence collection
4. Detection review
5. Investigation and mapping
6. Incident reporting
7. Lessons learned

## Published Scenario Index

| Scenario | Status | Summary |
|---|---|---|
| [`01-reconnaissance`](01-reconnaissance/README.md) | :white_check_mark: Completed | Primary reconnaissance case study is complete; advanced comparison variants are deferred until the full core phase sequence is published |
| [`02-execution`](02-execution/README.md) | :hourglass_flowing_sand: Planned | Three-variant execution detection track across Sysmon, PowerShell, and EDR/SIEM telemetry |
| [`03-credential-access`](03-credential-access/README.md) | :hourglass_flowing_sand: Planned | Two-variant credential access track across authentication and host-level telemetry |
| [`04-persistence`](04-persistence/README.md) | :hourglass_flowing_sand: Planned | Two-variant persistence track across registry and scheduled task evidence |
| [`05-privilege-escalation`](05-privilege-escalation/README.md) | :hourglass_flowing_sand: Planned | Single deep-dive privilege escalation case study |
| [`06-defense-evasion`](06-defense-evasion/README.md) | :hourglass_flowing_sand: Planned | Two-variant defense evasion track across obfuscation and tampering behavior |
| [`07-discovery-lateral-movement`](07-discovery-lateral-movement/README.md) | :hourglass_flowing_sand: Planned | Three-variant discovery and lateral movement track across endpoint and network visibility |
| [`08-collection`](08-collection/README.md) | :hourglass_flowing_sand: Planned | Two-variant collection track around staging and archive preparation activity |
| [`09-exfiltration`](09-exfiltration/README.md) | :hourglass_flowing_sand: Planned | Three-variant exfiltration track across egress, IDS, and EDR/SIEM coverage |

## Directory Contract

Every scenario should contain:

- `README.md` - primary case study narrative
- `commands.md` - exact commands used during the simulation
- `analysis.md` - analyst notes, timeline, and findings
- `incident-report.md` - scenario-specific incident report
- `evidence/screenshots/` - sanitized screenshots in ordered sequence

This structure keeps attack execution, evidence, analysis, and reporting reviewable as separate artifacts.
