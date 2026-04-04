1. Overview

Build a virtual Active Directory lab to simulate real-world attack scenarios.

2. Environment

Windows Server 2022 (Domain Controller) - 8gb RAM 4CPU  <img width="879" height="775" alt="Windows Server Environment " src="https://github.com/user-attachments/assets/1cc6e15f-6f58-47cb-a2f8-5889d8e651e2" />

Kali Linux (Attacker) - 4GB RAM, 2CPU  <img width="836" height="715" alt="Kali Environment" src="https://github.com/user-attachments/assets/d9cc9c0a-82df-4fe7-8b8b-e705751c5f6b" />


VirtualBox (Host-only network)    <img width="1884" height="706" alt="VB Host Only Network" src="https://github.com/user-attachments/assets/ef01b670-ec6f-4a58-ad47-fbfcb37361a8" />


4. Objectives:
First, the domain environment was scanned and user accounts were enumerated to identify potential targets. A simple Brute Force Attack was then executed to gain access to valid accounts, demonstrating domain compromise techniques.

Simulate weak credential attack
Perform a Brute Force attack
Demonstrate domain compromise techniques
<img width="937" height="506" alt="Weak Credential-BruteForce" src="https://github.com/user-attachments/assets/70c89196-43c4-4e70-ba3d-9f73079175c8" />



5. Key Findings
Weak passwords allow immediate domain access
Password spraying identifies vulnerable accounts
Improper account policies increase risk
