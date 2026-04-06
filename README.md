<div align="center">#
  ## Overview
</div>


This project simulates a real-world Active Directory (AD) environment and demonstrates how weak credentials can be exploited to gain unauthorized access to a domain.

The lab was built using a Windows Server 2022 Domain Controller and a Kali Linux attacker machine. The objective was to replicate a common initial access technique used in penetration testing and real-world cyber attacks.



<div align="center">
  Lab Environment:
</div>

Domain Controller: Windows Server 2022
Attacker Machine: Kali Linux
Virtualization: VirtualBox
Network Configuration: NAT + Host-Only Adapter


Network Configuration:
Domain Controller IP: 192.168.56.10
Attacker Machine IP: 192.168.56.30
Domain Name: lab.local

 <div align="center">
Active Directory Configuration:
 </div>

The domain environment was structured to reflect a simplified enterprise setup.

 <div align="center">
Organizational Units (OUs):
</div>

Employees
IT Admins
User Accounts:
Standard user accounts (e.g., jdoe, asmith)
Privileged account (admin1)
Misconfigured account (D1Test) with weak credentials

This misconfiguration was intentionally introduced to simulate a common enterprise security weakness.


Windows Server 2022 (Domain Controller) - 8gb RAM 4CPU  <img width="879" height="775" alt="Windows Server Environment " src="https://github.com/user-attachments/assets/1cc6e15f-6f58-47cb-a2f8-5889d8e651e2" />


Kali Linux (Attacker) - 4GB RAM, 2CPU  <img width="836" height="715" alt="Kali Environment" src="https://github.com/user-attachments/assets/d9cc9c0a-82df-4fe7-8b8b-e705751c5f6b" />


VirtualBox (Host-only network)    <img width="1884" height="706" alt="VB Host Only Network" src="https://github.com/user-attachments/assets/ef01b670-ec6f-4a58-ad47-fbfcb37361a8" />


<div align="center">
Attack: Credential-Based Initial Access
</div>

A credential validation attack was performed using NetExec to test authentication over the SMB protocol.

netexec smb 192.168.56.10 -u D1Test -p 'Password123'


<div align="center">
Attack Rationale:
</div>

SMB is a commonly exposed service in Windows environments and is frequently targeted by attackers for authentication-based attacks.

Weak or reused passwords significantly increase the likelihood of successful compromise during the initial access phase.


<div align="center">
Results:
</div>

Authentication was successfully achieved using weak credentials, demonstrating how easily a misconfigured account can be exploited.

This confirms that the domain is vulnerable to credential-based attacks.
<img width="937" height="506" alt="Weak Credential-BruteForce" src="https://github.com/user-attachments/assets/70c89196-43c4-4e70-ba3d-9f73079175c8" />

<div align="center">
Post-Exploitation Potential:
</div>

With valid domain credentials, an attacker could:

Enumerate domain users and groups
Access shared resources over SMB
Attempt privilege escalation
Perform lateral movement across systems

This highlights the risk associated with weak credential policies in Active Directory environments.


<div align="center">
Security Impact:
</div>

Weak passwords can lead to immediate unauthorized access
Compromised accounts can serve as an entry point for further attacks
Lack of proper account controls increases overall domain risk


<div align="center">
Mitigation Strategies:
</div>

The implementation of account policies such as password requirements, 2FA and MFA is necessary to stop attackers from brute force or password spraying attacks. 
Enforce strong password policies
Implement account lockout thresholds
Monitor authentication attempts and logs
Use Multi-Factor Authentication (MFA) where possible






