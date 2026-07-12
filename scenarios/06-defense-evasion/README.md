# Phase 6 - Defense Evasion

This phase will document how attacker behavior attempts to reduce visibility or bypass controls, and how those attempts can still be investigated.

## Defense Evasion Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-obfuscated-powershell-wazuh`](01-obfuscated-powershell-wazuh/README.md) | :hourglass_flowing_sand: Planned | Obfuscated execution telemetry + SIEM correlation | Obfuscated PowerShell or encoded execution investigated through endpoint and Wazuh evidence |
| [`02-defender-tampering-edr`](02-defender-tampering-edr/README.md) | :hourglass_flowing_sand: Planned | Endpoint protection tampering + EDR/SIEM perspective | Security control interference investigated through endpoint protection and SIEM visibility |

## Why This Phase Uses Two Variants

The highest-value comparison here is between hidden execution behavior and tampering with security controls. That pairing is strong enough without stretching the phase unnecessarily.
