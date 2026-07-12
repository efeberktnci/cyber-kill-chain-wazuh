# Phase 8 - Collection

This phase will document how data is staged, gathered, or prepared before exfiltration, and what defender evidence that activity creates.

## Collection Variants

| Variant | Status | Detection Lens | Summary |
|---|---|---|---|
| [`01-file-staging-wazuh`](01-file-staging-wazuh/README.md) | :hourglass_flowing_sand: Planned | File activity telemetry + SIEM correlation | File staging and suspicious preparation steps investigated through endpoint and Wazuh evidence |
| [`02-archive-collection-wazuh`](02-archive-collection-wazuh/README.md) | :hourglass_flowing_sand: Planned | Archive creation telemetry + SIEM correlation | Compression, archive building, and data preparation investigated through endpoint and SIEM evidence |

## Why This Phase Uses Two Variants

File staging and archive preparation capture the strongest pre-exfiltration behaviors without making the phase repetitive.
