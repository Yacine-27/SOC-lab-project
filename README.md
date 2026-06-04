# Home SOC Lab

A Security Operations Center (SOC) home lab built around Active Directory, Sysmon, PowerShell auditing, and Wazuh SIEM for centralized security monitoring and log analysis.

## Architecture

<img width="763" height="512" alt="thumbnail" src="https://github.com/user-attachments/assets/4059e66b-0636-4642-bf70-fc81533d768e" />

## Wazuh Dashboard

<img width="960" height="397" alt="wazuh-dashboard" src="https://github.com/user-attachments/assets/cdd03ddd-dd65-48a4-af38-ce6fc35b5138" />


## Key Features

- Active Directory domain with centralized policy management
- Sysmon deployment using the SwiftOnSecurity configuration
- PowerShell Module, Script Block, and Transcription logging via GPO
- Centralized log collection and analysis using Wazuh
- Agent-side event filtering to reduce SIEM noise
- Index State Management (ISM) policies for automated log retention

## Attack Simulations

The lab is used to emulate adversary activity and validate detection capabilities within Wazuh.

- [Reconnaissance](./playbooks/01-Reconnaissance/README.md)
- [Initial Access](./playbooks/02-initial-access/README.md)
- [Internal Discovery](./playbooks/03-internal-discovery/README.md)
- [Credential Harvesting](playbooks/04-credential-harvesting)
- [Lateral Movement](playbooks/05-lateral-movement/README.md)
- [Data Exfilteration](playbooks/06-data-exfiltration/README.md)

## Technologies

- Wazuh
- Active Directory
- Sysmon
- Windows Event Logging
- PowerShell
- Group Policy
- Ubuntu Server
- VMware Workstation
- Kali attack tools: nmap, hydra, xfreerdp, mimikatz.

 ## Future Planning

- Deploy Network-level IDS/IPS (Suricata, Zeek) to detect Network artifacts.
