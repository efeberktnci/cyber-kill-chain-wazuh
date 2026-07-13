# Detection Engineering

This directory stores the reusable detection content behind the case studies in this repository.

It is not only for rules. It is also the place where we explain:

- what telemetry source was used,
- what parser or decoder made the data usable,
- what detection logic produced the alert,
- what gaps still remain,
- what future tuning work is planned.

## Current Contents

- [`detection-coverage-matrix.md`](detection-coverage-matrix.md) - portfolio-wide coverage tracker that maps attack phases to telemetry, logic, and outcome status

## What Will Be Added Here

- Wazuh local rules and decoder snapshots tied to specific scenarios
- Query references used during investigation
- Sysmon and future endpoint telemetry references
- Sigma or cross-platform logic when the repository expands beyond Wazuh-only detections

## Publishing Standard

Every new detection artifact added here should document:

1. purpose
2. prerequisite telemetry
3. implementation location
4. validation evidence
5. false-positive considerations
6. tuning or rollback notes
