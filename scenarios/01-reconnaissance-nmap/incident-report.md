# Incident Report - IR-2026-001

## Document Control

| Field | Value |
|---|---|
| Status | Final |
| Severity | Low |
| Analyst | Efe Berktnci |
| Scenario ID | 01 |
| Detection Rule | `100101` |
| Report Date | 2026-07-07 |

## Executive Summary

A controlled reconnaissance action was executed from the Kali attacker VM against the Windows 10 victim using Nmap. The attacker targeted a small set of common Windows-related TCP service ports. The victim did not expose those services, and Windows Firewall blocked the inbound probes.

The key outcome was defensive visibility: Windows Firewall logs captured the blocked connections, and Wazuh correlated repeated drops from the same source IP into a level 10 alert: `PORT SCAN DETECTED: Multiple dropped firewall connections from 192.168.56.10 - Possible Nmap scan`.

No compromise occurred. The case study is significant because it demonstrates how a SOC can convert otherwise weak default recon visibility into a validated detection pipeline.

## Scope and Affected Assets

| Role | Asset | Address |
|---|---|---|
| Source | Kali attacker VM | `192.168.56.10` |
| Target | Windows 10 victim | `192.168.56.103` |
| Monitoring | Wazuh manager | `192.168.56.105` |

## Detection Source

- Primary victim-side source: `C:\Windows\System32\LogFiles\Firewall\pfirewall.log`
- Wazuh decoder: `windows-firewall`
- Base firewall event rule: `4101`
- Local correlation rule: `100101`

## Incident Timeline

| Time (UTC+03:00) | Source | Event | Analyst Assessment |
|---|---|---|---|
| 17:00 | Kali | Nmap TCP connect scan executed against `192.168.56.103` | Authorized reconnaissance simulation began |
| 16:59:56-16:59:58 | Windows Firewall log | Repeated `DROP TCP 192.168.56.10 192.168.56.103` entries for multiple destination ports | Victim blocked and recorded the scan |
| 17:00:35 onward | Wazuh | `rule.id:100101` generated | Repeated drop events correlated into reconnaissance alert |
| 17:19 | Wazuh event detail review | Attacker-attributed event reviewed in Threat Hunting | Alert instance confirmed as scenario evidence |

## Indicators and Evidence

### Source IP

- `192.168.56.10`

### Target IP

- `192.168.56.103`

### Targeted Ports

- `22`
- `135`
- `139`
- `445`
- `3389`

### Wazuh Rule

- `100101`

### Key Evidence Sources

- Kali terminal output
- Windows Firewall log
- Wazuh Threat Hunting event list
- Wazuh event detail for attacker-attributed correlation

## Investigation Findings

1. The attacker performed a controlled TCP reconnaissance action.
2. The target remained protected; all tested ports appeared filtered from the attacker perspective.
3. The Windows victim recorded repeated dropped connections from the attacker IP.
4. Wazuh successfully ingested the firewall log and generated a correlated detection.
5. Additional background lab traffic (`192.168.56.1`) triggered the same correlation logic, so analyst review was required to isolate the attacker-specific event.

## Root Cause

This activity was authorized lab simulation and not malicious compromise. The triggering condition was deliberate reconnaissance performed for SOC validation and portfolio development.

## Impact Assessment

| Area | Assessment |
|---|---|
| Confidentiality | No impact |
| Integrity | No impact |
| Availability | No impact |
| Exposure | No externally reachable service identified |
| Detection value | High |

## Severity Rationale

Severity is intentionally recorded as low because the scenario remained in the reconnaissance phase:

- there was no successful service access,
- there was no execution on the victim,
- there was no credential interaction,
- preventive controls functioned as expected,
- the primary security outcome was early detection rather than post-compromise response.

## Containment, Eradication, and Recovery

No containment or recovery action was required because:

- the activity occurred in an isolated authorized lab,
- the victim was not compromised,
- the blocked probes served as intended detection validation input.

## MITRE ATT&CK Mapping

| Tactic | Technique | ID | Rationale |
|---|---|---|---|
| Discovery | Network Service Discovery | T1046 | The attacker probed Windows-related TCP ports to learn service exposure. |

## Cyber Kill Chain Mapping

| Phase | Rationale |
|---|---|
| Reconnaissance | The attacker gathered pre-exploitation information about reachable network services. |

## Detection and Response Recommendations

1. Keep Windows Firewall logging enabled for controlled network-detection scenarios.
2. Retain the custom Wazuh decoder and local correlation rule as baseline lab content.
3. Tune the correlation rule to suppress known background traffic where appropriate.
4. Reuse this firewall-driven visibility method in later discovery and lateral-movement scenarios.

## Analyst Notes

- The alert stream included background lab traffic from `192.168.56.1`, so source-IP validation was required before selecting final evidence.
- The attacker-attributed correlation event for this report was the instance tied to `192.168.56.10 -> 192.168.56.103`.
- Preserving this distinction makes the case study more realistic and more useful for future tuning work.

## Lessons Learned

- Reconnaissance detection quality improved significantly only after explicit victim-side logging was added.
- A blocked scan can still produce excellent SOC evidence.
- Correlation rules should be validated against background lab noise before publication.
- Documenting visibility gaps and the engineering fix makes the portfolio stronger and more realistic.
