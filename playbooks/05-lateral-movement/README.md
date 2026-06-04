## Adversarial Emulation & Detection Phase 5 : Lateral Movement via Remote Desktop Protocol (RDP)

Following successful credential harvesting from the compromised Windows Client, this phase simulates lateral movement across the Active Directory environment using valid domain credentials (Lateral Movement:T1021.001 – Remote Desktop Protocol).

## Execution:
```
xfreerdp /u:"Administrator@DOMAIN" /p:"password>" /v:192.168.100.20
```
<img width="1676" height="821" alt="lateral-movement-exec" src="https://github.com/user-attachments/assets/0f94eab7-a73a-4787-a77f-6519d07341cb" />

## Detection:
 Looking for successful logons with Logon_type=10 (RDP connections)

 <img width="1517" height="456" alt="admin-rdp" src="https://github.com/user-attachments/assets/db5ddac7-b614-4ca7-9c99-5e16379a397d" />

 
