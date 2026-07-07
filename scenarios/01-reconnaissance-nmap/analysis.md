# Scenario 01 Analysis

## Analyst Goal

Determine whether a controlled Nmap reconnaissance action against the Windows victim can be observed from three perspectives:

1. attacker execution,
2. victim-side host evidence,
3. SIEM-side detection and investigation.

## Timeline

All timestamps below are lab local time (`UTC+03:00`) to match the captured evidence.

| Time | Source | Observation | Analyst Assessment |
|---|---|---|---|
| 16:59:56 | Windows Firewall log | `DROP TCP 192.168.56.10 192.168.56.103 ... 135` | Reconnaissance reached the victim and was blocked |
| 16:59:56 | Windows Firewall log | `DROP TCP 192.168.56.10 192.168.56.103 ... 445` | Additional service-oriented probe observed |
| 16:59:57 | Windows Firewall log | `DROP TCP 192.168.56.10 192.168.56.103 ... 445` | Repeated targeting supports scan pattern |
| 16:59:57 | Windows Firewall log | `DROP TCP 192.168.56.10 192.168.56.103 ... 135` | Same source IP, multiple destination ports |
| 16:59:58 | Windows Firewall log | `DROP TCP 192.168.56.10 192.168.56.103 ... 135/139` | Sustained inbound probing creates correlation candidate |
| 17:00:35 to 17:03:30 | Wazuh Threat Hunting | `rule.id:100101` repeatedly triggered | Defender-visible correlated reconnaissance alert confirmed |

## Findings

### 1. The attacker executed a real reconnaissance action

The Kali attacker successfully reached the victim with an Nmap TCP connect scan against ports `22`, `135`, `139`, `445`, and `3389`.

Observed attacker-side result:

- target online
- ports filtered
- no exposed service returned

This means the attacker did not gain service enumeration output, but the activity still created useful defensive signal.

### 2. The victim captured the important evidence

Windows Firewall logging recorded the key behavior directly:

- source IP: `192.168.56.10`
- destination IP: `192.168.56.103`
- action: `DROP`
- protocol: `TCP`
- destination ports included reconnaissance-relevant Windows exposure ports

This is the most important victim-side evidence because it shows the attack reached the host and was blocked by a native control.

### 3. Wazuh did not provide the desired story by default

Early testing showed that a strong recon narrative was not automatically available through default host telemetry alone. That gap mattered because the goal of the repository is not just to run attacks, but to build defensible SOC evidence.

The lab therefore required detection engineering to convert raw Windows Firewall data into a portfolio-grade alert.

### 4. Detection engineering closed the gap successfully

The final detection path was:

1. Windows Firewall logged dropped connections to `pfirewall.log`
2. the Windows Wazuh agent collected that file
3. a local decoder parsed key firewall fields
4. a local Wazuh rule correlated repeated firewall drops from the same source IP
5. Wazuh generated `rule.id:100101` with the description:

`PORT SCAN DETECTED: Multiple dropped firewall connections from 192.168.56.10 - Possible Nmap scan`

### 5. Background noise existed and had to be investigated

The same local rule also triggered on background traffic from `192.168.56.1`. That did not invalidate the detection, but it required analyst review to select the attacker-attributed event instance.

This is a useful portfolio detail because it shows the difference between:

- raw alert presence, and
- analyst attribution.

## False Positive and Noise Review

The lab generated additional dropped traffic from `192.168.56.1`, which also satisfied the correlation threshold in some cases. That behavior is important to preserve in the write-up because it reflects a realistic SOC workflow:

- detection logic may be technically correct,
- but analyst review is still required to attribute the alert to the intended adversary source,
- clean portfolio evidence comes from selecting the attacker-specific event instance rather than hiding the existence of noise.

In other words, the scenario demonstrates both detection capability and analyst judgment.

## Detection Assessment

| Question | Answer |
|---|---|
| Was the recon activity executed successfully? | Yes |
| Did the victim host record it? | Yes |
| Did the final Wazuh alert map to the real attacker IP? | Yes |
| Was analyst review required to separate attack traffic from background noise? | Yes |
| Does the final result support the scenario objective? | Yes |

## Why This Scenario Matters

This scenario demonstrates a realistic SOC engineering lesson:

> Sometimes the most valuable outcome is not the original scan result, but the work required to transform low-level telemetry into reliable detection.

That makes the case study stronger, not weaker.

## Severity Rationale

The scenario is assessed as low severity because:

- no code execution occurred,
- no credentials were accessed,
- no persistence was established,
- the victim remained protected,
- the most important outcome was early visibility into hostile recon behavior.

## Improvement Backlog

1. Tighten the local correlation rule to reduce noise from `192.168.56.1`.
2. Consider scoping the rule to the host-only subnet or target host where appropriate.
3. Evaluate whether additional Windows filtering or decoder refinement can improve signal quality.
4. Preserve the custom firewall-based visibility pattern as a reusable design for later network-oriented scenarios.
