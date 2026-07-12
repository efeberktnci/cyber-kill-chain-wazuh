# Phase 7 - Discovery and Lateral Movement

This phase will document how the attacker learns more about the environment and then attempts to move or reach additional systems.

## Discovery and Lateral Movement Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-host-discovery-wazuh`](01-host-discovery-wazuh/README.md) | :hourglass_flowing_sand: Planned | Host discovery telemetry + SIEM correlation | Local discovery commands and endpoint evidence investigated through Wazuh |
| [`02-remote-access-wazuh`](02-remote-access-wazuh/README.md) | :hourglass_flowing_sand: Planned | Remote access telemetry + SIEM correlation | Remote access attempts and their authentication or process evidence investigated in Wazuh |
| [`03-network-lateral-movement`](03-network-lateral-movement/README.md) | :hourglass_flowing_sand: Planned | Network movement visibility + SIEM/IDS perspective | Lateral movement indicators compared across network and endpoint evidence |

## Why This Phase Uses Three Variants

This phase naturally spans local host discovery, remote session establishment, and network movement. Those are meaningfully different stories and deserve separate case studies.
