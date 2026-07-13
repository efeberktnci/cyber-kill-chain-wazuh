# Detection Coverage Matrix

This matrix tracks what the lab can currently detect, how the detection works, and which engineering gaps still remain.

It is intentionally portfolio-oriented: the goal is to show not just that an alert fired, but which telemetry source, parsing path, and logic layer made that alert possible.

## Reading the Matrix

- `Coverage status` reflects whether the primary case study for that phase is already validated.
- `Telemetry source` identifies the evidence path that the defender actually relied on.
- `Detection implementation` points to the rule, decoder, or logic layer responsible for the alert.
- `Current state` distinguishes between completed primary coverage and deferred comparison variants.

## Core Phase Coverage

| Phase | Scenario / Variant | Attack behavior | Telemetry source | Detection implementation | Rule / Logic ID | MITRE ATT&CK | Coverage status | Current state | Notes |
|---|---|---|---|---|---|---|---|---|---|
| Phase 1 - Reconnaissance | [`01-windows-firewall-wazuh`](../scenarios/01-reconnaissance/01-windows-firewall-wazuh/README.md) | Controlled Nmap TCP recon against common Windows service ports | Windows Firewall log at `C:\Windows\System32\LogFiles\Firewall\pfirewall.log` collected by the Wazuh agent | Custom Windows Firewall decoder + Wazuh correlation rule on repeated drops from the same source IP | Base `4101`, correlated alert `100101` | T1046 - Network Service Discovery | :white_check_mark: Validated | :white_check_mark: Completed primary variant | Default Sysmon + Wazuh visibility did not provide a clean inbound scan narrative. Detection quality improved after enabling firewall logging, ingesting `pfirewall.log`, and correlating repeated drop events. |
| Phase 1 - Reconnaissance | [`02-suricata-wazuh`](../scenarios/01-reconnaissance/02-suricata-wazuh/README.md) | Same recon objective viewed through network IDS telemetry | Suricata EVE / IDS alerts (planned) | Planned Suricata + Wazuh alert handling | Planned | T1046 - Network Service Discovery | :hourglass_flowing_sand: Not yet validated | Deferred comparison variant | Will be implemented after all primary attack phases are published so the project keeps momentum without sacrificing future telemetry comparison depth. |
| Phase 1 - Reconnaissance | [`03-edr-siem`](../scenarios/01-reconnaissance/03-edr-siem/README.md) | Same recon objective viewed through endpoint / EDR telemetry | Endpoint detection and process/network telemetry (planned) | Planned EDR + SIEM comparison workflow | Planned | T1046 - Network Service Discovery | :hourglass_flowing_sand: Not yet validated | Deferred comparison variant | Reserved for later comparison against the completed host-firewall-based story. |
| Phase 2 - Execution | [`02-execution`](../scenarios/02-execution/README.md) | Controlled Windows command and PowerShell execution | Sysmon, PowerShell logging, and future comparison telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Primary execution case study will be the next core phase after reconnaissance. |
| Phase 3 - Credential Access | [`03-credential-access`](../scenarios/03-credential-access/README.md) | Authentication and credential abuse activity | Authentication + host telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Will focus on signals that are understandable to beginner analysts and still professionally defensible. |
| Phase 4 - Persistence | [`04-persistence`](../scenarios/04-persistence/README.md) | Registry and scheduled task persistence | Host telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Intended to compare two distinct persistence lenses without redundant screenshots. |
| Phase 5 - Privilege Escalation | [`05-privilege-escalation`](../scenarios/05-privilege-escalation/README.md) | Focused local privilege escalation case study | Host telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Designed as a single deeper case study rather than multiple shallow variants. |
| Phase 6 - Defense Evasion | [`06-defense-evasion`](../scenarios/06-defense-evasion/README.md) | Obfuscation and tampering behavior | Host telemetry + security-control visibility | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Will emphasize analyst interpretation, not just alert generation. |
| Phase 7 - Discovery and Lateral Movement | [`07-discovery-lateral-movement`](../scenarios/07-discovery-lateral-movement/README.md) | Host discovery and remote movement activity | Endpoint and network telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | This phase is intentionally broader because movement behavior changes meaningfully across evidence sources. |
| Phase 8 - Collection | [`08-collection`](../scenarios/08-collection/README.md) | Local staging and archive preparation | Host telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Will track what the adversary gathered and how the defender can prove it. |
| Phase 9 - Exfiltration | [`09-exfiltration`](../scenarios/09-exfiltration/README.md) | Data egress and transfer behavior | Host, IDS, and EDR/SIEM telemetry | Planned | Planned | Planned | :hourglass_flowing_sand: Not yet validated | Planned | Reserved for the final attack-phase comparison work before the unified SOC report. |

## Phase 1 Detection Engineering Takeaway

Phase 1 already demonstrates an important professional lesson:

> an attacker action does not become a useful SOC story until the right telemetry source, parser, and correlation logic are aligned.

In this repository, the reconnaissance phase became portfolio-grade only after we:

1. identified a visibility gap,
2. changed the evidence source,
3. validated parsing,
4. wrote correlation logic,
5. confirmed the alert in Wazuh with attacker-attributed evidence.

## Directory Relationship

- `scenarios/` contains the full case-study narrative
- `detections/` contains reusable logic, coverage tracking, and detection engineering context
- `reports/` will later aggregate cross-scenario findings
- `diagrams/` will later visualize telemetry flow and detection paths
