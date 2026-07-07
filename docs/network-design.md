# Network Design

## Design Goals

- Permit only the connectivity required for attack simulation and telemetry collection.
- Keep the lab isolated from unauthorized targets and production networks.
- Make addressing and traffic paths reproducible for future analysts.

## Current Topology

The lab is built on a dual-network VirtualBox model:

- NAT network for outbound Internet access, package installation, and update feeds
- Host-only network for analyst-controlled traffic between Kali, Windows, and Wazuh

Windows ICMP rules permit diagnostic ping traffic on the host-only segment. Kali successfully reached both the Windows endpoint and the Wazuh server during baseline validation.

## Network Inventory

| Asset | Interface / Adapter | Address | Gateway | DNS | Purpose |
|---|---|---|---|---|---|
| Kali Linux | `eth0` (NAT) | `10.0.2.15/24` | `10.0.2.2` | Internet-resolved | Internet access and package retrieval |
| Kali Linux | `eth1` (Host-only) | `192.168.56.10/24` | None | None required | Attack simulation |
| Windows victim | Adapter 1 (NAT) | `10.0.2.15/24` | VirtualBox NAT | DHCP-provided | Internet access and updates |
| Windows victim | Adapter 2 (Host-only) | `192.168.56.103/24` | None | Host-only DHCP-provided | Monitored endpoint |
| Wazuh server | `enp0s3` (NAT) | `10.0.2.15/24` | `10.0.2.2` | `1.1.1.2`, `1.0.0.2` observed during validation | Feed updates and package retrieval |
| Wazuh server | `enp0s8` (Host-only) | `192.168.56.105/24` | None | None required | SIEM services for the lab |

## Routing Notes

- Repeated `10.0.2.15` assignments are normal in VirtualBox NAT mode because each guest uses an isolated NAT context.
- The host-only segment is the authoritative path for attack simulation and east-west validation.
- The Wazuh server default route must remain on `enp0s3`; when that DHCP lease is lost, feed downloads and NTP break.

## Required Validation

- Confirm the lab subnet and rule out unintended bridged exposure before publishing new scenarios.
- Record any future changes to host-only addressing or adapter order.
- Preserve timestamp alignment whenever VM clocks drift or NAT connectivity resets.
- Re-validate Wazuh ingestion after major Sysmon or Wazuh configuration changes.
