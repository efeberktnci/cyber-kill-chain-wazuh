# Detection Engineering

This directory is organized by attack phase so coverage stays clean as the project grows from Phase 1 through Phase 9.

## Detection Coverage Index

| Phase | Status | Coverage File |
|---|---|---|
| Phase 1 - Reconnaissance | :white_check_mark: Completed | [`phase-01-reconnaissance/README.md`](phase-01-reconnaissance/README.md) |
| Phase 2 - Execution | :hourglass_flowing_sand: Planned | [`phase-02-execution/README.md`](phase-02-execution/README.md) |
| Phase 3 - Credential Access | :hourglass_flowing_sand: Planned | [`phase-03-credential-access/README.md`](phase-03-credential-access/README.md) |
| Phase 4 - Persistence | :hourglass_flowing_sand: Planned | [`phase-04-persistence/README.md`](phase-04-persistence/README.md) |
| Phase 5 - Privilege Escalation | :hourglass_flowing_sand: Planned | [`phase-05-privilege-escalation/README.md`](phase-05-privilege-escalation/README.md) |
| Phase 6 - Defense Evasion | :hourglass_flowing_sand: Planned | [`phase-06-defense-evasion/README.md`](phase-06-defense-evasion/README.md) |
| Phase 7 - Discovery and Lateral Movement | :hourglass_flowing_sand: Planned | [`phase-07-discovery-lateral-movement/README.md`](phase-07-discovery-lateral-movement/README.md) |
| Phase 8 - Collection | :hourglass_flowing_sand: Planned | [`phase-08-collection/README.md`](phase-08-collection/README.md) |
| Phase 9 - Exfiltration | :hourglass_flowing_sand: Planned | [`phase-09-exfiltration/README.md`](phase-09-exfiltration/README.md) |

## Why This Layout Exists

The original single wide matrix was difficult to read in GitHub preview. The repository now uses:

- a narrow top-level coverage index,
- one dedicated detection summary file per phase,
- space inside each phase folder for future rules, queries, Sigma logic, and tuning notes.

This is more maintainable and more professional than storing the matrix only as an image.

## What Belongs Here

Each phase folder can later hold:

- rule summaries
- local decoder notes
- investigation queries
- false-positive notes
- tuning backlog
- future Sigma or cross-platform detection logic

