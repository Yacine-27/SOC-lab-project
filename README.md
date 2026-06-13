# Home SOC Lab

A Security Operations Center (SOC) home lab built around Active Directory, Sysmon, PowerShell auditing, Suricata IDS, and Wazuh SIEM for centralized security monitoring, threat detection, and log analysis.

## Architecture

<img width="768" height="512" alt="architecture" src="https://github.com/user-attachments/assets/ba43bea8-6d96-4ac6-81a0-2579a7d23e1d" />


## Wazuh Dashboard

<img width="960" height="397" alt="wazuh-dashboard" src="https://github.com/user-attachments/assets/cdd03ddd-dd65-48a4-af38-ce6fc35b5138" />


## Key Features

- Active Directory domain with centralized policy management.
- Sysmon deployment using the SwiftOnSecurity configuration.
- PowerShell Script Block, and Transcription logging via GPO.
- Suricata network intrusion detection and traffic monitoring.
- Centralized log collection and analysis using Wazuh.
- Agent-side event filtering to reduce SIEM noise.
- Index State Management (ISM) policies for automated log retention.

## Attack Simulations

The lab is used to emulate adversary activity and validate detection capabilities within Wazuh.

- [Reconnaissance](./playbooks/01-Reconnaissance/README.md)
- [Initial Access](./playbooks/02-initial-access/README.md)
- [Internal Discovery](./playbooks/03-internal-discovery/README.md)
- Credential Harvesting [kerboroasting](playbooks/04-credential-harvesting/01-kerboroasting/README.md) [lsass dumping](playbooks/04-credential-harvesting/02-lsass-dumping/README.md)
- [Lateral Movement](playbooks/05-lateral-movement/README.md)
- [Data Exfilteration](playbooks/06-data-exfiltration/README.md)

## Technologies

- Wazuh
- Suricata IDS
- Active Directory
- Sysmon
- Windows Event Logging
- PowerShell
- Group Policy
- Ubuntu Server
- VMware Workstation
- Kali attack tools: nmap, hydra, xfreerdp, mimikatz, getuserspn hashcat.

 ## Future Planning

- Build custom Wazuh detection rules.
