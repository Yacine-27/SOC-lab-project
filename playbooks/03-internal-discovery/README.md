# Adversarial Emulation & Detection Engineering — Phase 03: Internal Discovery

## 1. Tactical Objective & Attack Methodology
Following a successful initial foothold via credential exploitation, this phase emulates an interactive post-compromise scenario. The attacker leverages Remote Desktop Protocol (RDP) from the external platform to log into the compromised Windows client. Once authenticated, the attacker executes local and Active Directory discovery commands to map out system processes, domain infrastructure, and high-value target groups (e.g., Domain Admins).

This simulation validates the visibility of host-level Sysmon configurations and advanced PowerShell Group Policy Object (GPO) audit policies under an interactive threat model.

### Adversarial Emulation Pipeline

#### Interactive Session Establishment
The attacker establishes an interactive RDP session using valid harvested domain credentials via `xfreerdp`:

```bash
xfreerdp /u:ad_user /p:SecurePassword123 /v:192.168.100.40
```
<img width="1912" height="819" alt="internal" src="https://github.com/user-attachments/assets/8fe30ae7-1eae-429f-b5c9-d2b832667bc7" />

### Detection:

Looking for rdp connection from the attacker ip (192.168.100.30) to target (192.168.100.40)

<img width="1508" height="667" alt="int3" src="https://github.com/user-attachments/assets/1c798db1-6d4f-4a15-9771-86389b126014" />

Looking or discovery commands using Powershell:

<img width="1512" height="572" alt="int 5" src="https://github.com/user-attachments/assets/500ead48-d71d-4364-b3a9-b1f18f3ab11d" />

Looking for discovery command on the target:

<img width="1920" height="1030" alt="int 6" src="https://github.com/user-attachments/assets/940702f3-7455-4b69-8954-7091e60d9bfc" />
