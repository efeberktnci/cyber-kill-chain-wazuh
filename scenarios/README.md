# Scenario Case Studies

Each numbered directory is a self-contained case study that follows the same analyst workflow:

1. Objective and lab scope
2. Controlled attack simulation
3. Endpoint and Wazuh evidence collection
4. Detection review
5. Investigation and mapping
6. Incident reporting
7. Lessons learned

## Published / Active Scenarios

| Scenario | Status | Summary |
|---|---|---|
| [`01-reconnaissance`](01-reconnaissance/README.md) | ✅ In Progress | Multi-variant reconnaissance detection phase with Windows Firewall + Wazuh completed first |

## Directory Contract

Every scenario should contain:

- `README.md` - primary case study narrative
- `commands.md` - exact commands used during the simulation
- `analysis.md` - analyst notes, timeline, and findings
- `incident-report.md` - scenario-specific incident report
- `evidence/screenshots/` - sanitized screenshots in ordered sequence

This structure keeps attack execution, evidence, analysis, and reporting reviewable as separate artifacts.
