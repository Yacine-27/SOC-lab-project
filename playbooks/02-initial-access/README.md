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

## 2. Detection

A spike in failed logons detected on target machine:

<img width="1916" height="787" alt="Brute force on endpoint detected" src="https://github.com/user-attachments/assets/26808e3e-ac76-40dc-aa08-736af23898ee" />

Successful network logon detected:

<img width="1455" height="612" alt="successful network logon" src="https://github.com/user-attachments/assets/4918ec05-f400-4557-9a2f-dab5f9998d86" />

Filtering for command ran on the attacker machine:

<img width="1920" height="772" alt="Brute force commands detected" src="https://github.com/user-attachments/assets/28fa05b4-d76e-495c-bb3f-54ba836b97f3" />

