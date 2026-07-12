# Phase 9 - Exfiltration

This phase will document controlled outbound transfer behavior and how it is investigated from host, network, and endpoint-detection perspectives.

## Exfiltration Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-dns-http-egress-wazuh`](01-dns-http-egress-wazuh/README.md) | :hourglass_flowing_sand: Planned | Host egress telemetry + SIEM correlation | DNS or HTTP/S egress activity investigated through host-level telemetry and Wazuh |
| [`02-network-ids-exfiltration`](02-network-ids-exfiltration/README.md) | :hourglass_flowing_sand: Planned | Network IDS telemetry + SIEM correlation | Exfiltration indicators observed from the network layer and investigated in the SIEM |
| [`03-edr-siem-exfiltration`](03-edr-siem-exfiltration/README.md) | :hourglass_flowing_sand: Planned | Endpoint detection + SIEM perspective | Exfiltration behavior reviewed from endpoint detection and SIEM perspectives together |

## Why This Phase Uses Three Variants

Exfiltration is one of the best places to compare host, network, and EDR-backed visibility because outbound behavior can look materially different in each telemetry source.
