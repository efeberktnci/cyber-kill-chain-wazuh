# Phase 1 Summary Report - Reconnaissance

## Executive Summary

Phase 1 validated that the lab can transform controlled reconnaissance into a defensible SOC detection story. The most important result was not the Nmap output itself, but the successful engineering of a victim-side telemetry path that allowed Wazuh to correlate repeated blocked probes into a port-scan alert.

## Phase Scope

| Area | Outcome |
|---|---|
| Attack simulation | Completed |
| Victim-side evidence collection | Completed |
| Wazuh ingestion | Completed |
| Custom correlation logic | Completed |
| Investigation and mapping | Completed |
| Cross-variant comparison | Deferred |

## Completed Primary Variant

| Variant | Status | Key Detection Outcome |
|---|---|---|
| `01-windows-firewall-wazuh` | :white_check_mark: Completed | `rule.id:100101` validated as attacker-attributed port-scan alert |

## Core Analyst Findings

1. Default visibility was not enough for a clean inbound reconnaissance story.
2. Windows Firewall logging became the decisive evidence source.
3. Wazuh correlation logic successfully elevated repeated drop events into a usable alert.
4. Background noise existed, so analyst attribution was still required.

## Detection Engineering Value

This phase demonstrates a professional blue-team lesson:

> detection quality depends on selecting the right telemetry source, not just deploying a SIEM.

That makes Phase 1 stronger than a basic "ran Nmap and got an alert" homelab walkthrough.

## MITRE ATT&CK Coverage

| Tactic | Technique | ID |
|---|---|---|
| Discovery | Network Service Discovery | T1046 |

## Cyber Kill Chain Coverage

| Phase | Mapped Activity |
|---|---|
| Reconnaissance | Host and service exposure probing before exploitation |

## Phase-Level Lessons Learned

- A blocked action can still be excellent SOC evidence.
- Victim-native telemetry can outperform default endpoint-only visibility for certain recon scenarios.
- Correlation rules should always be reviewed against lab noise before publication.
- Detection engineering decisions are worth documenting as first-class portfolio artifacts.

## Deferred Work

The reconnaissance phase is complete at the primary case-study level. The following comparison work is intentionally deferred until the remaining core attack phases are published:

- Suricata + Wazuh reconnaissance comparison
- EDR / SIEM reconnaissance comparison
- final cross-variant fidelity and noise review
