# Git Workflow

## Branches

- `main` contains reviewed, reproducible project state.
- Short-lived branches use `docs/`, `scenario/`, `detection/`, or `fix/` prefixes.
- A scenario branch should cover one case study or one bounded improvement.

## Commit Standard

Use imperative, scoped messages that describe one reviewable outcome.

Examples:

- `chore: establish project foundation`
- `docs: document validated lab topology`
- `scenario: add Nmap reconnaissance case study`
- `detection: add Wazuh rule for suspicious PowerShell`
- `fix: correct ATT&CK technique mapping`

Do not mix generated evidence, detection changes, and unrelated documentation cleanup in one commit.

## Scenario Quality Gate

Before merging a scenario, verify:

- Commands and prerequisites are reproducible.
- Evidence follows the naming and screenshot standard.
- Detection logic and investigation findings are supported by observable data.
- ATT&CK and Cyber Kill Chain mappings include rationale.
- Incident report and lessons learned are complete.
- Secrets, credentials, and unrelated personal data are absent.

