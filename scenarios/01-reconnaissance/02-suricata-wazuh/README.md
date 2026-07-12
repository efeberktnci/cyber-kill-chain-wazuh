# Reconnaissance Variant 02 - Suricata + Wazuh

## Status

:hourglass_flowing_sand: Planned.

## Objective

Re-run the same reconnaissance theme from Kali and validate how network IDS telemetry changes the defender story when Suricata is introduced alongside Wazuh.

## Planned Value

This variant is intended to answer a different question from the Windows Firewall case study:

- What does reconnaissance look like from the network sensor perspective?
- Which alerts become easier to identify when packet and flow inspection are available?
- How does network-based detection compare with host-based drop-log correlation?

## Planned Deliverables

- attack execution evidence
- Suricata alert evidence
- Wazuh ingestion and investigation evidence
- MITRE ATT&CK mapping
- comparison notes against Variant 01

## Planned Detection Focus

- network-layer scan visibility
- signature-driven or traffic-pattern detection
- contrast between IDS alerting and host-based firewall artifacts
