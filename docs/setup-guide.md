## Network Architecture:
**Environment:** VMware Workstation isolated host-only network (`192.168.100.0/24`).
**SIEM Node:** Ubuntu Server (`192.168.100.10`) running central Wazuh Manager and Indexer.
**Domain Controller:** Windows Server 2022 (`192.168.100.20`) handling aauthentication and serving GPOs.
**Endpoint Node:** Windows 10 Client (`192.168.100.40`) domain-joined for user activity tracking.

## PowerShell Auditing via GPO:
Configured specialized Group Policy Objects (GPOs) to record deep script execution telemetry:
**Module Logging (Event ID 4103):** Records pipeline initialization steps and module details.
**Script Block Logging (Event ID 4104):** Captures full, un-obfuscated script content directly in memory right before execution.

## Sysmon Telemetry Integration
Installed System Monitor (Sysmon) utilizing the SwiftOnSecurity configuration framework.
* **Process Creation (Event ID 1):** Tracks parent-to-child relationship dynamics to identify anomalous execution vectors.
* **Network Tracking (Event ID 3):** Maps inbound and outbound TCP/UDP traffic directly to the executing process hash.

## Log Fine-Tuning & Noise Reduction
**Targeted Filtering:** Modified the client side `ossec.conf` file to drop verbose, non-security background noise at the host source.
