# Adversarial Emulation & Detection Engineering — Phase 01: Network Reconnaissance

## 1. Tactical Objective & Attack Methodology
Prior to launching targeted credential-guessing or initial access vectors, an adversary must establish situational awareness within the compromised or adjacent subnet. This phase emulates **MITRE ATT&CK T1046 (Network Service Discovery)** and maps to the **Reconnaissance** phase of the Cyber Kill Chain.

To identify active assets across the isolated host-only subnet without interacting heavily with application layers, a horizontal ping sweep was executed from the attack platform.

### Attacker Execution (Kali Linux)
The following command was issued from the attack machine (`192.168.100.30`) to discover live hosts within the `192.168.100.0/24` range:

```bash
nmap -sn 192.168.100.0/24
```

<img width="1686" height="653" alt="01" src="https://github.com/user-attachments/assets/61fa5cfd-2f65-4063-b509-d1e24fabb4b5" />

## Detection

Filtering for commands ran by the attacker machine:

<img width="1916" height="647" alt="02" src="https://github.com/user-attachments/assets/32c0a286-6017-4881-a200-7708e7ef862a" />

### Detection Gap Analysis

Sysmon Event ID 3 was not generated on target machines because:
- Remote port scans don't create process-originated network events on the target
- This is a known detection blind spot for host-based agents

### Future Detection Controls to Enhance Visiblity:
- Network-level IDS/IPS (Zeek)
