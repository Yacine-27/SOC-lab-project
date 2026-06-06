# Adversarial Emulation & Detection - Phase 02: Initial Access

## 1. Tactical Objective
The objective of this phase is to simulate an external threat actor attempting to gain an initial foothold on an enterprise workstation via credential guessing. This exercise validates the SIEM's capability to ingest, parse, and alert on high-frequency authentication anomalies.

**Target Asset:** Windows 10 Client (`192.168.100.40`)
**Attacking Platform:** Kali Linux (`192.168.100.30`)
**Vector:** RDP Authentication Services
**MITRE ATT&CK Mapping:** T1110.001 (Brute Force: Password Guessing)

## 2. Execution (Adversarial Emulation)
Using Hydra on the attacking platform, a network-based password-guessing attack was launched against the target workstation utilizing a custom dictionary block:

```bash
hydra -L users.txt -P passwords.txt rdp://192.168.100.40 -V
```

<img width="1141" height="197" alt="execution" src="https://github.com/user-attachments/assets/165a9721-deed-43ac-8914-ca25c5319bff" />

## 2. Detection

A spike in failed logons detected on target machine:

<img width="1502" height="792" alt="failed" src="https://github.com/user-attachments/assets/44f773dc-4cfa-42ab-93a2-94c36b875169" />


Successful network logon detected:

<img width="1485" height="602" alt="success" src="https://github.com/user-attachments/assets/6ed2a82e-f7bf-4d58-900b-d18a770345d7" />

Looking in the IDS alerts:

<img width="1493" height="722" alt="suricata" src="https://github.com/user-attachments/assets/5432995c-5575-4849-8696-8360bc6ab45a" />


Filtering for command ran on the attacker machine:

<img width="1920" height="772" alt="Brute force commands detected" src="https://github.com/user-attachments/assets/28fa05b4-d76e-495c-bb3f-54ba836b97f3" />

