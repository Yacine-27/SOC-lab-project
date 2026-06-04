# Adversarial Emulation & Detection Engineering — Phase 03: Internal Discovery

## 1. Tactical Objective & Attack Methodology
Following a successful initial foothold via credential exploitation, the attacker leverages Remote Desktop Protocol (RDP) from the external platform to log into the compromised Windows client. Once authenticated, the attacker executes local and Active Directory discovery commands to map out system processes and domain infrastructure.

This simulation validates the visibility of host-level Sysmon configurations and advanced PowerShell Group Policy Object (GPO) audit policies under an interactive threat model.

#### Interactive Session Establishment
The attacker establishes an interactive RDP session using valid harvested domain credentials via `xfreerdp`:

```bash
xfreerdp /u:client@DOMAIN /p:<password> /v:192.168.100.40
```
<img width="1907" height="537" alt="client-rdp-redacted" src="https://github.com/user-attachments/assets/4971352e-6b94-4c8c-b731-ea4be291bf77" />


### Detection:

Looking for rdp connection from the attacker ip (192.168.100.30) to target (192.168.100.40)

<img width="1487" height="465" alt="client-rdp-connection" src="https://github.com/user-attachments/assets/26bd61ac-32fc-49ec-85da-165c5b39d873" />

Looking or discovery commands using Powershell:

<img width="1512" height="572" alt="int 5" src="https://github.com/user-attachments/assets/500ead48-d71d-4364-b3a9-b1f18f3ab11d" />

Looking for discovery command on the target:

<img width="1920" height="1030" alt="int 6" src="https://github.com/user-attachments/assets/940702f3-7455-4b69-8954-7091e60d9bfc" />
