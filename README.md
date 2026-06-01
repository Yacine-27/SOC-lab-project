This project demonstrates the deployment of a (SOC) home lab environment. It features an Active Directory domain, comprehensive endpoint auditing via Sysmon and PowerShell GPOs, and centralized log analysis utilizing an enterprise-grade open-source SIEM (Wazuh).
Network Architecture & Topology:

<img width="575" height="340" alt="network-diagram" src="https://github.com/user-attachments/assets/8e0c48fe-1bd3-48ec-9cad-85d0a5428688" />

Core Implementation Details:
1. Telemetry & Auditing Enhancement
Sysmon Deployment: Implemented SwiftOnSecurity Sysmon configuration to capture deep endpoint telemetry (Process creation, network connections).
Group Policy Objects (GPO): Enforced advanced PowerShell logging (Module, Script Block, and Transcription logging) across the domain.

2. SIEM Fine-Tuning
Optimized agent `ossec.conf` files to filter out high-volume benign Windows events, ensuring efficient bandwidth usage and focusing strictly on security-relevant event IDs.

3. Storage Optimization 
To prevent disk exhaustion on the Wazuh-Server due to high-volume Windows Sysmon and PowerShell logs, I implemented a custom Index State Management (ISM) policy within the Wazuh Indexer to set retention lifecycle.
