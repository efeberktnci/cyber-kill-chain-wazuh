# Phase 1 Reconnaissance - Analyst Workflow

```mermaid
flowchart TD
    A["Run controlled recon from Kali"] --> B["Confirm victim-side firewall drops"]
    B --> C["Search Wazuh for rule.id:100101"]
    C --> D["Review event list for attacker-attributed entries"]
    D --> E["Open document details"]
    E --> F["Validate srcip = 192.168.56.10"]
    F --> G["Validate dstip = 192.168.56.103"]
    G --> H["Validate targeted ports match attack set"]
    H --> I["Record evidence and timeline"]
    I --> J["Map to MITRE T1046 and Kill Chain Reconnaissance"]
```

## Interpretation

This workflow highlights a real analyst lesson: an alert existing is not enough. The analyst still has to separate attacker-attributed evidence from lab background noise.
