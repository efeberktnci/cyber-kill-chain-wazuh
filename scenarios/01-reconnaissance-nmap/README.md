# Scenario 01 - Reconnaissance - Nmap Discovery

## Executive Summary

This case study will document a controlled reconnaissance action from the Kali attacker VM to the Windows victim. The goal is to show how early-stage discovery activity can be executed safely, traced in telemetry, reviewed in Wazuh, and translated into analyst-ready documentation.

## Why This Scenario Comes First

Reconnaissance is the safest and most natural first attack phase for the lab because:

- it creates recognizable network and endpoint activity without immediately changing the victim state
- it teaches the relationship between attacker actions and defender visibility
- it establishes the workflow we will reuse in every later case study

## Objective and Scope

### Objective

Perform a controlled Nmap-based discovery action from Kali against the Windows victim and determine what is visible from the SOC perspective.

### Scope

- Source system: Kali attacker VM
- Target system: Windows 10 victim
- Monitoring platform: Wazuh server
- Allowed activity: lab-only host discovery and limited service discovery

## Lab Context

| Role | Host | Address |
|---|---|---|
| Attacker | Kali | `192.168.56.10` |
| Victim | Windows 10 | `192.168.56.103` |
| SIEM | Wazuh | `192.168.56.105` |

## Preconditions and Safety Controls

- Phase 1 baseline must be complete before execution.
- All activity must remain inside the host-only lab subnet.
- No scans may target systems outside `192.168.56.0/24`.
- Commands must be recorded exactly in `commands.md`.
- Evidence must follow the screenshot standard already defined for this repository.

## Attack Plan

This scenario will likely be executed in two small steps:

1. Host discovery or simple reachability validation
2. Limited port / service discovery against the Windows victim

The exact commands will be added after we choose the safest first Nmap options together.

## Expected Telemetry

We expect to review at least some combination of the following:

- Windows Defender Firewall or network-related Windows events
- Sysmon network-related telemetry if the current config captures it
- Wazuh alerts or raw searchable events connected to reconnaissance behavior

## Detection Questions

This scenario is meant to answer beginner-friendly SOC questions:

- Can Wazuh see the reconnaissance activity directly?
- If not directly, can we still find supporting evidence in raw events?
- Which part of the telemetry chain sees the behavior best: endpoint, Wazuh rule, or both?
- What detection gaps remain after the first scan?

## Evidence Plan

The expected screenshot flow for this scenario is:

1. Attack command on Kali
2. Attack result on Kali
3. Endpoint-side evidence on Windows if available
4. Wazuh event or alert list
5. Wazuh event detail
6. Analyst notes / mapping evidence if needed

## MITRE ATT&CK Mapping

| Tactic | Technique | ID | Mapping Rationale |
|---|---|---|---|
| Reconnaissance | Active Scanning | T1595 | Nmap-based discovery activity fits active target scanning behavior |

## Cyber Kill Chain Mapping

| Phase | Mapping Rationale |
|---|---|
| Reconnaissance | The activity gathers information about the target before exploitation |

## Detection Gaps and Improvements

To be completed after execution.

## Incident Response

To be completed after execution.

## Lessons Learned

To be completed after execution.
