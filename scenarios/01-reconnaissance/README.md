# Phase 1 - Reconnaissance

This phase is now structured as a multi-telemetry detection study. The same attacker objective is preserved across each sub-scenario: controlled reconnaissance against the Windows victim from Kali, followed by defender-side validation in the monitoring stack.

The goal is not to repeat screenshots for the sake of repetition. The goal is to compare how the same reconnaissance behavior appears through different defensive lenses:

- host-based telemetry
- network-based telemetry
- endpoint detection and response telemetry

## Reconnaissance Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-windows-firewall-wazuh`](01-windows-firewall-wazuh/README.md) | ✅ Completed | Host-based firewall telemetry + SIEM correlation | Windows Firewall drop logging ingested into Wazuh and correlated into `rule.id:100101` |
| [`02-suricata-wazuh`](02-suricata-wazuh/README.md) | ⏳ Planned | Network IDS telemetry + SIEM correlation | Suricata-based recon visibility and alert handling in Wazuh |
| [`03-edr-siem`](03-edr-siem/README.md) | ⏳ Planned | Endpoint detection + SIEM perspective | Endpoint/EDR process and network visibility compared against SIEM findings |

## Why This Structure Matters

This phase is intentionally stronger than a single-tool walkthrough. It demonstrates that reconnaissance detection quality depends on telemetry coverage, not just on the SIEM platform itself.

By keeping the attack objective constant and changing the evidence source, the project can later compare:

- detection fidelity
- investigation depth
- analyst confidence
- noise levels
- visibility gaps

## Reading Order

1. Start with [`01-windows-firewall-wazuh`](01-windows-firewall-wazuh/README.md) for the implemented baseline recon case study.
2. Use the planned variants as the roadmap for expanding coverage across network IDS and EDR perspectives.
3. Review the final comparison section once all recon variants are complete.
