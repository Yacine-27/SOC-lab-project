Adversarial Emulation & Detection: Authentication Brute-Force

## 1. Tactical Objective
The objective of this phase is to simulate an external threat actor attempting to gain an initial foothold on an enterprise workstation via credential guessing. This exercise validates the SIEM's capability to ingest, parse, and alert on high-frequency authentication anomalies.

**Target Asset:** Windows 10 Client (`192.168.100.40`)
**Attacking Platform:** Kali Linux (`192.168.100.30`)
**Vector:** RDP / SMB Authentication Services
**MITRE ATT&CK Mapping:** T1110.001 (Brute Force: Password Guessing)

## 2. Execution (Adversarial Emulation)
Using Hydra on the attacking platform, a network-based password-guessing attack was launched against the target workstation utilizing a custom dictionary block:

```bash
hydra -L users.txt -P passwords.txt rdp://192.168.100.40 -V
```
<img width="1632" height="348" alt="Successful attack" src="https://github.com/user-attachments/assets/633d548f-a18a-4a47-863a-a5b1eceefb38" />
