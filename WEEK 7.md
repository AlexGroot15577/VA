Ques%on 1: Analyse packet1.pcap and find the flag. 
<img width="595" height="419" alt="image" src="https://github.com/user-attachments/assets/72796e27-0ff8-40e1-89dd-1dfe6832eb79" />
Ques%on 2: Analyse packet2.pcap and find the flag. 
<img width="595" height="369" alt="image" src="https://github.com/user-attachments/assets/efdf1545-91f1-45d1-bacc-9fef0c3d58e3" />
Ques%on 3: Interpret an Nmap Output

What can an attacker do with each port? 

-Port 21 (FTP)
→ Upload/download files, brute-force login, anonymous access

-Port 22 (SSH)
→ Remote login, brute-force attack

-Port 80 (HTTP)
→ Web attacks (XSS, SQL Injection, directory traversal)

-Port 139 (NetBIOS)
→ Enumerate users, shared resources

-Port 445 (SMB)
→ Access shared files, remote exploitation

What vulnerabilities are likely present based on the version? 

-vsftpd 2.3.4 → Backdoor vulnerability

-OpenSSH 5.3p1 → Outdated, weak encryption

-Apache 2.2.8 → Known exploits (RCE, DoS)

-SMB (Windows 7) → EternalBlue (MS17-010)

-NetBIOS → Information disclosure

Which one is the highest risk and why? 

Port 445 (SMB)

-Vulnerable to EternalBlue exploit

-Allows Remote Code Execution (RCE)

-Widely used in attacks like WannaCry

What attack path can be built from this?

1. Scan target (Nmap)
2. Exploit SMB (Port 445)
3. Gain system access
4. Escalate privileges
5. Move laterally in network

What should be the remediation?

-Patch Windows system (MS17-010)

-Disable SMBv1

-Close unused ports (21, 139)

-Update Apache & SSH

-Use firewall and strong authentication

Ques%on 4: Iden%fy the OS (OS Fingerprin%ng) - TTL 
<img width="507" height="178" alt="image" src="https://github.com/user-attachments/assets/78f8b192-8526-4f47-8b5b-cf5a577ea906" />
TTL = 64 → Linux/Unix

Linux systems commonly use a default TTL of 64. After a few hops, the value remains close to 64, indicating a Unix-based OS.

<img width="283" height="193" alt="image" src="https://github.com/user-attachments/assets/c60cfb39-07b9-4c3b-8a4d-101c02ffec3d" />
TTL = 128 → Windows

Windows operating systems use a default TTL of 128. The observed value suggests the packet originated from a Windows machine.

<img width="518" height="119" alt="image" src="https://github.com/user-attachments/assets/dbdaaebe-08b5-4a5c-a1cc-6b39e3059783" />
TTL = 255 → Network Device (Router/Cisco)

Network devices such as routers typically use a default TTL of 255, indicating the packet likely comes from a networking device.

Ques%on 5: Analyse the Nessus file 
<img width="1809" height="808" alt="image" src="https://github.com/user-attachments/assets/7c88df4d-4d6c-4404-97ec-e713f55dabeb" />
1.	What is the affected Port number
   
Port 8009

2.	What is the Affected protocol

AJP (Apache JServ Protocol)

3. What is the CVSS Score of vulnerability found  

9.8 Critical

4. Can you find any exploit related to this vulnerability?

Yes, ghostcat allows attackers to read sensitive files from the server and may lead to Remote Code Execution (RCE) if exploited.

5. Find CVE for this vulnerability.

CVE-2020-1938
