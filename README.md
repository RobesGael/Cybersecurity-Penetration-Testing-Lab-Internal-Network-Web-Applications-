# Cybersecurity-Penetration-Testing-Lab-Internal-Network-Web-Applications


## Project Overview
This project simulates a real-world enterprise penetration test performed in a controlled lab environment. The objective is to demonstrate offensive security skills across:
•	Network reconnaissance and enumeration 
•	Web application penetration testing (OWASP Juice Shop) 
•	API security assessment 
•	Windows and Linux service analysis 
•	Vulnerability exploitation and reporting 
•	Risk analysis using CVSS v3.1 and MITRE ATT&CK 
The assessment follows the NIST SP 800-115 methodology, aligned with real-world consulting penetration testing practices.


## Scope of Engagement
#### In-Scope Assets
  Asset	          IP Address	     Role
- Kali Linux	    192.168.1.203	   Attacker Machine
- Windows 11	    192.168.1.136	   User Workstation
- Windows Server	192.168.1.219	   Enterprise Server
- Ubuntu Server	  192.168.1.145	   Web Application Host (OWASP Juice Shop)
- Wazuh SIEM	    192.168.1.105	   Security Monitoring System


#### Network Scope
- Testing type: Internal penetration test 
- Attack position: Same-network attacker 

#### In-Scope Services
- Web applications (3000) 
- SMB (445) 
- RDP (3389) 
- WinRM (5985) 
- SSH (22) 
- RPC (135) 
- WSDAPI (5357) 


#### Out of Scope 
- Physical security testing 
- External internet infrastructure 
- Social engineering attacks 


## Rules of Engagement
- No intentional service disruption 
- No data deletion or corruption 
- No persistence mechanisms deployed 
- Testing performed in an isolated lab environment only 
- All activity is authorized for educational purposes 


## Objectives
- Identify vulnerabilities across network and application layers 
- Perform full attack surface mapping 
- Exploit OWASP Top 10 vulnerabilities 
- Evaluate Windows service exposure risks 
- Demonstrate lateral movement potential 
- Document findings in a professional security report format 


## Lab Architecture
Attacker: Kali Linux
IP: 192.168.1.203

Targets:
- Windows 11: 192.168.1.136
- Windows Server: 192.168.1.219
- Ubuntu Server (Juice Shop): 192.168.1.145
- SIEM (Wazuh): 192.168.1.105


## Methodology (NIST SP 800-115)
1.	Planning & Scoping 
2.	Reconnaissance 
3.	Scanning & Enumeration 
4.	Vulnerability Analysis 
5.	Exploitation 
6.	Post-Exploitation Analysis 
7.	Reporting 


## Tools Used
- Network & Enumeration
•	Nmap 
•	Gobuster 
 
- Web Application Security
•	Burp Suite 
•	OWASP Juice Shop 
•	Browser DevTools 

- Infrastructure Analysis
•	SSH enumeration scripts 
•	SMB/RDP probing tools 
•	WinRM testing utilities 
________________________________________
🚨 Key Findings Summary
Severity	Count
Critical	2
High	7
Medium	1
________________________________________
📊 Key Vulnerabilities
🔴 Critical
•	SQL Injection (Authentication Bypass) 
•	SQL Injection (Search Function) 
🟠 High
•	Insecure Direct Object Reference (IDOR) 
•	Business Logic Manipulation 
•	Sensitive Data Exposure (/rest/memories) 
•	Cross-Site Scripting (XSS) 
•	Confidential File Exposure (/ftp/acquisition) 
🟡 Medium
•	API Overexposure (/api/quantity) 
________________________________________
🧪 Attack Scenarios Demonstrated
💉 SQL Injection (Auth Bypass)
•	Authentication bypass via SQL injection payload 
•	Unauthorized login without credentials 
🔁 IDOR Exploitation
•	Access to other users’ basket data via ID manipulation 
💰 Business Logic Abuse
•	Negative quantity manipulation resulting in wallet credit abuse 
🌐 XSS Exploitation
•	JavaScript execution in browser context via search functionality 
________________________________________
🧭 MITRE ATT&CK Mapping
Technique	ID	Description
Exploit Public-Facing Application	T1190	SQL Injection attacks
Remote Services Exploitation	T1210	IDOR abuse
Data from Information Repositories	T1213	API data exposure
Command & Scripting Interpreter	T1059.007	XSS execution
Abuse Elevation Control Mechanism	T1548	Business logic manipulation
________________________________________
📉 CVSS v3.1 Risk Ratings
Vulnerability	Score	Severity
SQL Injection (Auth Bypass)	9.8	Critical
SQL Injection (Search)	9.1	Critical
IDOR	8.1	High
Sensitive Data Exposure	8.6	High
Business Logic Flaw	7.5	High
XSS	7.4	High
File Exposure	7.8	High
API Overexposure	4.3	Medium
________________________________________
📈 Key Security Insights
•	Broken Access Control was the primary systemic weakness 
•	Web application layer represented the highest attack surface 
•	Internal Windows services exposed lateral movement opportunities 
•	Business logic flaws allowed financial manipulation scenarios 
•	API design lacked proper authorization enforcement 
________________________________________
🛠️ Recommendations Summary
Immediate Actions
•	Remediate SQL Injection vulnerabilities using parameterized queries 
•	Remove sensitive data (password hashes) from API responses 
•	Strengthen authentication mechanisms 
High Priority
•	Implement Role-Based Access Control (RBAC) 
•	Fix IDOR vulnerabilities across all endpoints 
•	Enforce strict server-side business logic validation 
•	Secure file access controls 
Infrastructure Hardening
•	Disable unnecessary services (WinRM, WSDAPI if not required) 
•	Enforce SMB signing and secure configuration 
•	Restrict RDP access to trusted networks only 
________________________________________
📌 Conclusion
The assessment identified multiple high and critical vulnerabilities across application and infrastructure layers.
If present in a production environment, these weaknesses could lead to:
•	Full system compromise 
•	Sensitive data exposure 
•	Financial manipulation 
•	Unauthorized administrative access 
•	Regulatory and compliance violations 


## Skills Demonstrated
•	Network penetration testing 
•	Web application security testing 
•	API security analysis 
•	Windows/Linux enumeration 
•	OWASP Top 10 exploitation 
•	Vulnerability reporting (NIST format) 
•	CVSS risk modeling 
•	MITRE ATT&CK mapping 


## Author
Robes Fokoueng


## Disclaimer
This project was conducted in a controlled and isolated lab environment for educational and professional development purposes only. No real-world systems were targeted.

