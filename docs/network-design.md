# Network Design

## Design Goals

- Permit only the connectivity required for attack simulation and telemetry collection.
- Keep the lab isolated from unauthorized targets and production networks.
- Make addressing and traffic paths reproducible for future analysts.

## Current Topology

Kali Linux, the Windows victim, and the Ubuntu Wazuh server can communicate inside the VirtualBox lab. Windows ICMP rules permit diagnostic ping traffic. Exact adapter modes, subnets, addresses, gateways, and DNS settings must be recorded after validation.

## Network Inventory

| Asset | Interface / Adapter | Address | Gateway | DNS | Purpose |
|---|---|---|---|---|---|
| Kali Linux | To be verified | To be verified | To be verified | To be verified | Attack simulation |
| Windows victim | To be verified | To be verified | To be verified | To be verified | Monitored endpoint |
| Wazuh server | To be verified | To be verified | To be verified | To be verified | SIEM services |

## Required Validation

- Record VirtualBox adapter mode for every VM.
- Confirm the lab subnet and rule out unintended bridged exposure.
- Record Wazuh agent enrollment and event transport paths.
- Verify host and VM time synchronization.
- Document any Internet access and why it is required.

