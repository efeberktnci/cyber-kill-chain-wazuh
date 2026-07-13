# Phase 1 Detection Coverage - Reconnaissance

## Coverage Summary

| Field | Value |
|---|---|
| Phase status | :white_check_mark: Completed |
| Primary variant | [`01-windows-firewall-wazuh`](../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/README.md) |
| Attack behavior | Controlled Nmap TCP reconnaissance against common Windows service ports |
| Telemetry source | `C:\Windows\System32\LogFiles\Firewall\pfirewall.log` |
| Collection path | Windows Wazuh agent log collection |
| Detection implementation | Custom Windows Firewall decoder + Wazuh correlation logic |
| Detection IDs | Base rule `4101`, correlated alert `100101` |
| MITRE ATT&CK | `T1046 - Network Service Discovery` |
| Analyst outcome | Attacker-attributed port-scan alert validated in Wazuh |

## What Was Learned

- Default Sysmon + Wazuh visibility did not provide a clean inbound-scan story for this scenario.
- Windows Firewall drop logging produced the strongest victim-side evidence.
- Repeated drops from the same source IP were correlated into a defender-usable port-scan alert.
- Background lab noise existed, so analyst validation of the attacker IP remained necessary.

## Implemented Variant

| Variant | Lens | Status | Why It Matters |
|---|---|---|---|
| `01-windows-firewall-wazuh` | Host firewall + SIEM correlation | :white_check_mark: Completed | Proves that recon can be turned into a strong SOC story by changing the telemetry source and writing detection logic |

## Deferred Comparison Variants

| Variant | Lens | Status | Reason Deferred |
|---|---|---|---|
| `02-suricata-wazuh` | Network IDS + SIEM | :hourglass_flowing_sand: Planned | Will be implemented after the primary case study from every core phase is complete |
| `03-edr-siem` | Endpoint / EDR + SIEM | :hourglass_flowing_sand: Planned | Reserved for later comparison against the completed firewall-based storyline |

## Supporting Scenario Artifacts

- Scenario narrative: [`../../scenarios/01-reconnaissance/README.md`](../../scenarios/01-reconnaissance/README.md)
- Primary case study: [`../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/README.md`](../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/README.md)
- Scenario commands: [`../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/commands.md`](../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/commands.md)
- Analyst notes: [`../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/analysis.md`](../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/analysis.md)
- Incident report: [`../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/incident-report.md`](../../scenarios/01-reconnaissance/01-windows-firewall-wazuh/incident-report.md)
