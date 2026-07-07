# Scenario 01 Commands

This file records the final commands used to execute, validate, and investigate the published reconnaissance case study.

## 1. Attacker Execution - Kali

```bash
nmap -Pn -sT -p 135,139,445,3389,22 192.168.56.103
```

Purpose:

- perform controlled TCP reconnaissance against common Windows-related service ports
- create predictable victim-side firewall telemetry
- keep the command short, explainable, and easy to reproduce

## 2. Victim Validation - Windows Firewall Logging

```powershell
netsh advfirewall show allprofiles logging
```

Purpose:

- verify that dropped connection logging is enabled before relying on `pfirewall.log` as evidence

## 3. Victim Evidence Review - Raw Tail

```powershell
Get-Content "C:\Windows\System32\LogFiles\Firewall\pfirewall.log" -Tail 50
```

Purpose:

- review recent firewall activity directly on the victim
- confirm that dropped TCP connections were recorded during the scan window

## 4. Victim Evidence Review - Filtered for Attacker to Victim

```powershell
Select-String -Path "C:\Windows\System32\LogFiles\Firewall\pfirewall.log" -Pattern "192.168.56.10 192.168.56.103"
```

Purpose:

- isolate attacker-to-victim drop events from unrelated background traffic
- produce cleaner evidence for the incident record

## 5. Wazuh Threat Hunting Query

```text
rule.id:100101
```

Purpose:

- retrieve correlated reconnaissance alerts generated from repeated firewall drop events

## 6. Detection Engineering Validation - Wazuh Rule Loader

```bash
sudo /var/ossec/bin/wazuh-analysisd -t
```

Purpose:

- validate that local Wazuh rules and decoders load successfully after detection engineering changes

## 7. Detection Engineering Validation - Wazuh Logtest

```bash
sudo /var/ossec/bin/wazuh-logtest
```

Representative test lines used during validation:

```text
2026-07-07 15:31:58 DROP TCP 192.168.56.106 192.168.56.103 50001 135 40 - - - - - - - RECEIVE
2026-07-07 15:31:59 DROP TCP 192.168.56.106 192.168.56.103 50002 139 40 - - - - - - - RECEIVE
2026-07-07 15:32:00 DROP TCP 192.168.56.106 192.168.56.103 50003 445 40 - - - - - - - RECEIVE
2026-07-07 15:32:01 DROP TCP 192.168.56.106 192.168.56.103 50004 3389 40 - - - - - - - RECEIVE
2026-07-07 15:32:02 DROP TCP 192.168.56.106 192.168.56.103 50005 22 40 - - - - - - - RECEIVE
```

Purpose:

- confirm that the custom decoder parses firewall log fields correctly
- confirm that repeated firewall drop events escalate into `rule.id:100101`

## 8. Detection Logic Implemented

The final custom logic was built around:

- built-in Wazuh firewall drop rule: `4101`
- local correlation rule: `100101`
- frequency threshold: `5`
- timeframe: `30` seconds
- grouping key: same source IP

This produced the final alert:

`PORT SCAN DETECTED: Multiple dropped firewall connections from <srcip> - Possible Nmap scan`
