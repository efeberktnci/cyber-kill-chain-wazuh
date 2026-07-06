# Screenshot and Evidence Standard

## Required Sequence

1. `01-attack-command`
2. `02-attack-result`
3. `03-endpoint-event`
4. `04-wazuh-alert`
5. `05-event-details`
6. `06-analyst-query`
7. `07-mapping`

## Rules

- Use PNG format and a consistent 16:9 or full-window capture.
- Capture the relevant application window, not the entire host desktop when avoidable.
- Ensure timestamps, hostname, event/rule ID, and relevant fields are readable.
- Redact credentials, tokens, personal data, and unrelated infrastructure details.
- Do not crop away context needed to establish provenance.
- Use lowercase kebab-case filenames with two-digit ordering.
- Add a short caption explaining what the evidence proves; never rely on the image alone.
- Store only scenario-specific images in that scenario's `evidence/screenshots/` directory.

## Example

`01-attack-command-nmap-service-scan.png`

The caption must state the source asset, UTC timestamp, action, and evidentiary significance.

