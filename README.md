<div align="center">
  <h2><strong>Overview</strong></h2> 
</div>

<div>
    This project simulates a real-world Active Directory (AD) environment and demonstrates how weak credentials can be exploited to gain unauthorized access to a domain.
The lab was built using a Windows Server 2022 Domain Controller and a Kali Linux attacker machine. The objective was to replicate a common initial access technique used in penetration testing and real-world cyber attacks.
</div>


<div align="center">
  <h2><strong>Lab Environment</strong></h2>
</div>

<div align="center">Domain Controller
</div>
Windows Server 2022 - 8gb RAM 4CPU  

<img width="879" height="775" alt="Windows Server Environment " src="https://github.com/user-attachments/assets/1cc6e15f-6f58-47cb-a2f8-5889d8e651e2" />



<div align="center">Attacker Machine
</div>

Kali Linux - 4GB RAM, 2CPU  

<img width="836" height="715" alt="Kali Environment" src="https://github.com/user-attachments/assets/d9cc9c0a-82df-4fe7-8b8b-e705751c5f6b" />

<div align="center">VirtualBoxNetwork Configuration 
</div>

NAT + Host-Only Adapter

<img width="1117" height="968" alt="VB Network Host Only Adapter" src="https://github.com/user-attachments/assets/579d6afb-3e82-4a40-87e5-0785408d8460" />


<div align="center">Network Configuration
</div>

Domain Controller IP: 192.168.56.10

<img width="752" height="362" alt="Windows Server 2022 IPconfig" src="https://github.com/user-attachments/assets/26343198-09b9-48fe-9674-a2460bb9cc48" />


Attacker Machine IP: 192.168.56.30

<img width="892" height="313" alt="Kali IP Address" src="https://github.com/user-attachments/assets/5079235a-7085-4080-bba7-d5eab31417d1" />


Domain Name: lab.local

<img width="751" height="320" alt="AD Domain" src="https://github.com/user-attachments/assets/60c7a229-dc2a-44c7-979d-43af446b2814" />


 <div align="center">
<h2><strong>Active Directory Configuration</strong></h2>
 </div>

The domain environment was structured to reflect a simplified enterprise setup.

<img width="943" height="689" alt="Server Manager Dashboard" src="https://github.com/user-attachments/assets/e55b9268-a281-4706-9542-1169f4a84fc3" />


 <div align="center">
<h2><strong>Organizational Units (OUs)</strong></h2>
</div>

Administration

<img width="755" height="289" alt="Admin Alice" src="https://github.com/user-attachments/assets/59c9dedf-7254-47af-b7fc-d9c0703d4125" />

Employees, standard user accounts (e.g., jdoe, asmith), privileged account (admin2), misconfigured account (D1Test) with weak credentials. This misconfiguration was intentionally introduced to simulate a common enterprise security weakness.

<img width="752" height="291" alt="Employees" src="https://github.com/user-attachments/assets/d9a0786c-07b7-4b00-8675-4e553e2f0d01" />



<div align="center">
<h2><strong>Attack: Credential-Based Initial Access</strong></h2>
</div>

<div> A network connectivity test was first performed using ICMP (ping) to verify that the target system (192.168.56.10) was reachable from the attacker machine. This step ensures that the host is online and accessible before attempting authentication-based attacks.

Following successful connectivity verification, a credential validation attack was performed using NetExec to test authentication over the SMB protocol.

netexec smb 192.168.56.10 -u D1Test -p 'Password123'
</div>


<img width="937" height="506" alt="Weak Credential-BruteForce" src="https://github.com/user-attachments/assets/70c89196-43c4-4e70-ba3d-9f73079175c8" />


<div align="center">
<h2><strong>Attack Rationale</strong></h2>
</div>

SMB is a commonly exposed service in Windows environments and is frequently targeted by attackers for authentication-based attacks.

Weak or reused passwords significantly increase the likelihood of successful compromise during the initial access phase.


<div align="center">
<h2><strong>Results</strong></h2>
</div>

Authentication was successfully achieved using weak credentials, demonstrating how easily a misconfigured account can be exploited.

This confirms that the domain is vulnerable to credential-based attacks.

<img width="937" height="147" alt="Brute Force Success" src="https://github.com/user-attachments/assets/dc4146f9-873d-4285-8fcc-391154e770b6" />


<div align="center">
<h2><strong>Post-Exploitation Potential</strong></h2>
</div>

With valid domain credentials, an attacker could
* Enumerate domain users and groups
* Access shared resources over SMB
* Attempt privilege escalation
* Perform lateral movement across systems

This highlights the risk associated with weak credential policies in Active Directory environments.


<div align="center">
<h2><strong>Security Impact</strong></h2>
</div>

* Weak passwords can lead to immediate unauthorized access 
* Compromised accounts can serve as an entry point for further attacks
* Lack of proper account controls increases overall domain risk


<div align="center">
<h2><strong>Mitigation Strategies</strong></h2>
</div>

* Enforce strong password policies
* Implement account lockout thresholds
* Monitor authentication attempts and logs
* Use Multi-Factor Authentication (MFA) where possible






