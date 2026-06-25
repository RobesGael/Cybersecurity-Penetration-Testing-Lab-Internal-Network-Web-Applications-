# Cybersecurity-Penetration-Testing-Lab-Internal-Network-Web-Applications


## Project Overview
This project simulates a real-world enterprise penetration test performed in a controlled lab environment. The objective is to demonstrate offensive security skills across:
- Network reconnaissance and enumeration 
- Web application penetration testing (OWASP Juice Shop) 
- API security assessment 
- Windows and Linux service analysis 
- Vulnerability exploitation and reporting 
- Risk analysis using CVSS v3.1 and MITRE ATT&CK 
The assessment follows the NIST SP 800-115 methodology, aligned with real-world consulting penetration testing practices.


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

  
## Phase 1: Planning & Scoping


### a- Scope of Engagement
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


### b- Rules of Engagement
- No intentional service disruption 
- No data deletion or corruption 
- No persistence mechanisms deployed 
- Testing performed in an isolated lab environment only 
- All activity is authorized for educational purposes 


### c- Objectives
- Identify vulnerabilities across network and application layers 
- Perform full attack surface mapping 
- Exploit OWASP Top 10 vulnerabilities 
- Evaluate Windows service exposure risks 
- Demonstrate lateral movement potential 
- Document findings in a professional security report format 



## Phase 2: Reconnaissance

#### Host Discovery
![image alt](https://github.com/RobesGael/Cybersecurity-Penetration-Testing-Lab-Internal-Network-Web-Applications-/blob/91f9a1bda10b1e7c6f0400bff88bea39922affcc/1-DISCOVERY.png)
<img width="832" height="203" alt="Image" src="https://github.com/user-attachments/assets/e4126c5b-1dcd-43a0-87b0-35003c5a5f7d" />
<img width="897" height="407" alt="Image" src="https://github.com/user-attachments/assets/8cb86bcc-7d83-48b6-9496-0c55f846ae93" />
<img width="823" height="196" alt="Image" src="https://github.com/user-attachments/assets/161b3a24-9312-4dbb-bf05-36517947617a" />

#### Service Discovery
<img width="1135" height="860" alt="Image" src="https://github.com/user-attachments/assets/97d3e990-78c1-4b57-9020-4d6b0044dad0" />
<img width="1408" height="862" alt="Image" src="https://github.com/user-attachments/assets/0119d6b2-8824-439a-8801-7fa03eef0b77" />
<img width="1401" height="788" alt="Image" src="https://github.com/user-attachments/assets/e69422bb-19d5-44e5-823a-157da25c593b" />


## Phase 3: Scanning & Enumeration 

#### a- Windows 11 (WIN 11/192.168.1.136)

Services Identified:
- TCP/445 – SMB
<img width="875" height="393" alt="Image" src="https://github.com/user-attachments/assets/e0e06826-2ab8-4bb2-a4e8-fffea3699ba9" />
<img width="818" height="271" alt="Image" src="https://github.com/user-attachments/assets/3c489b38-1dd5-417d-811e-a7be68d71b6d" />

- TCP/135 – MSRPC
<img width="1013" height="237" alt="Image" src="https://github.com/user-attachments/assets/ece850ef-b448-46da-9458-6fe2fe573c83" />


#### b- Windows server (WIN 11/192.168.1.219)
Services Identified:
- TCP/3389 – RDP
<img width="972" height="586" alt="Image" src="https://github.com/user-attachments/assets/91249a4a-5caf-4309-9a30-5b316ba4a6fb" />

- TCP/139 & 445
<img width="728" height="281" alt="Image" src="https://github.com/user-attachments/assets/74b63bed-3f99-425d-98cf-a0de079556e5" />
<img width="908" height="355" alt="Image" src="https://github.com/user-attachments/assets/c10a8e70-f125-4820-be3e-9a1bf87f2cbb" />
<img width="917" height="422" alt="Image" src="https://github.com/user-attachments/assets/679c9347-9f85-4f00-b73d-b14c9ac7f139" />

- TCP/135 - RPC
<img width="676" height="88" alt="Image" src="https://github.com/user-attachments/assets/c4704af9-ffe9-4352-9cdb-e9ff0918f1ef" />

- TCP/5357 - WSDAPI
<img width="872" height="196" alt="Image" src="https://github.com/user-attachments/assets/99f5e275-4815-4409-880e-093c491aa9b0" />

- TCP/5985 - WSMAN
<img width="882" height="196" alt="Image" src="https://github.com/user-attachments/assets/5a3da13f-2eaa-4a66-b376-d9a2b947f74d" />


#### c- Ubuntu Server (Target3/192.168.1.145)
Services Identified:

- TCP/22 - SSH
<img width="780" height="787" alt="Image" src="https://github.com/user-attachments/assets/f93b2dbc-b8b2-4dd5-9019-ac8ba0b2b486" />
<img width="762" height="247" alt="Image" src="https://github.com/user-attachments/assets/eccc60fb-08e2-4aed-9556-93e9710c90cb" />
<img width="822" height="262" alt="Image" src="https://github.com/user-attachments/assets/2fa0f956-3f53-4ae2-a849-fcbef6af16ac" />

- TCP/3000 - Web application (HTTP/OWASP Juice Shop)

HTTP Response Headers:

<img width="715" height="307" alt="Image" src="https://github.com/user-attachments/assets/8c8b6d8e-8d25-4df2-b1ac-f4b9c8c122f7" />

Web Technology Fingerprinting:

<img width="1897" height="207" alt="Image" src="https://github.com/user-attachments/assets/3c881983-fc6d-471f-a16a-0019a0e82172" />

Gobuster - Directory Enumeration:

<img width="705" height="712" alt="Image" src="https://github.com/user-attachments/assets/37a99067-9ed0-41c2-97f5-e10ee6921355" />

## Phase 4: Vulnerability Analysis
Objectives

Identify vulnerabilities and determine their impact.

Key Findings
SQL Injection
Broken Access Control
IDOR
Sensitive Data Exposure
Business Logic Manipulation
Cross-Site Scripting
Confidential File Exposure




## Phase 5: Exploitation
### 1. Feedback Access Control Weakness

#### My customer Feedback
<img width="623" height="551" alt="Image" src="https://github.com/user-attachments/assets/2fa75903-974c-4428-91d2-d5eb8400a44c" />

#### Request and Reponse (Feedback id = 50)
<img width="1385" height="516" alt="Image" src="https://github.com/user-attachments/assets/f2e9eaa5-adc3-47a9-ae4e-348938b88bf1" />

#### In Burp Suite Repeater, I resent the original request without modification. The server accepted it and generated a new feedback entry with ID 51.
<img width="1300" height="556" alt="Image" src="https://github.com/user-attachments/assets/3a5410a8-7a61-43b1-8d35-2c72224a3c92" />

#### In Burp Suite Repeater, after sending the modified request(Comment and rating), the server created a new feedback entry with ID 52.
<img width="1257" height="632" alt="Image" src="https://github.com/user-attachments/assets/15b7db02-4173-4d24-831a-207185bf6a58" />

### 2. Sensitive Data Exposure

#### The GET /rest/memory/ HTTP/1.1 endpoint leaks other users information in its response, resulting in unauthorized disclosure of user data.
<img width="1420" height="638" alt="Image" src="https://github.com/user-attachments/assets/30f728aa-e937-4fe6-9f83-2fb132ee0bc6" />

<img width="1430" height="692" alt="Image" src="https://github.com/user-attachments/assets/924d3e86-2c59-457c-aa2b-eeaec58088a6" />



### 3. API Overexposure (/api/quantity)

#### The GET /rest/quantity endpoint leaks internal stock quantities, allowing unauthorized users to access inventory information.
<img width="1452" height="721" alt="Image" src="https://github.com/user-attachments/assets/41522525-41e8-41d1-9faa-0499a95adc3f" />
<img width="1442" height="747" alt="Image" src="https://github.com/user-attachments/assets/af4cc708-c0e2-4bed-a9b7-e26755c7a8cb" />

### 4. IDOR in Basket API
#### The basket endpoints allow unauthorized access to other users’ baskets simply by modifying the basket ID in the request.

My Basket.
<img width="1358" height="571" alt="Image" src="https://github.com/user-attachments/assets/dbd0c92a-b355-4c5d-b740-a326dc4f8b00" />

Other users' baskets.
<img width="1447" height="692" alt="Image" src="https://github.com/user-attachments/assets/b4422b9d-a5a5-4b69-9ee0-86746ffe82ec" />
<img width="1430" height="682" alt="Image" src="https://github.com/user-attachments/assets/65b7d0ba-3774-4414-8305-b8dae5331852" />

### 5. Business Logic Vulnerability

#### The application allows quantity manipulation, including negative values, enabling unauthorized price manipulation and invalid purchases.

#### I added product ID 12 to my basket, then used Burp Repeater to modify the quantity to 2 and later to –3. The server accepted both values, and I was able to complete checkout successfully.

<img width="1292" height="543" alt="Image" src="https://github.com/user-attachments/assets/3f9b4105-60e3-49ad-b233-10c576dbaf12" />

-
<img width="1372" height="591" alt="Image" src="https://github.com/user-attachments/assets/df9f6d85-efcb-48ed-84b9-57f4bdc38e84" />

-
<img width="1227" height="680" alt="Image" src="https://github.com/user-attachments/assets/2f5c85aa-83c6-490f-ac63-2202fc9ecd39" />

-
<img width="1451" height="566" alt="Image" src="https://github.com/user-attachments/assets/c6e80706-b6bb-40a5-81fc-3863b50d9df9" />

-
<img width="1345" height="666" alt="Image" src="https://github.com/user-attachments/assets/c2f43516-fdd6-4ed6-afba-83ac8711c6cd" />

-
<img width="1252" height="541" alt="Image" src="https://github.com/user-attachments/assets/e78b19ec-9aa0-4fdc-b4bd-830030a0d776" />


### 6. Confidential File Exposure
The /ftp endpoint allows unauthorized access to confidential documents by modifying the file path, indicating directory traversal and broken access control.

Steps:

- Sent GET /ftp/legal.md
- Modified the request to GET /ftp/ to reveal the list of available documents
- Identified additional files such as acquisition.md
- Sent GET /ftp/acquisition.md and successfully accessed a confidential document

<img width="1317" height="756" alt="Image" src="https://github.com/user-attachments/assets/39aecd74-7ab9-4d29-add8-76ce686bc25b" />

-

<img width="1312" height="740" alt="Image" src="https://github.com/user-attachments/assets/bcc3021f-8bd1-446f-954a-d9fffe9586f0" />

-
<img width="1266" height="742" alt="Image" src="https://github.com/user-attachments/assets/9a458655-db46-48cb-aca4-b2545bcb0931" />


### 7. SQL Injection Authentication Bypass

#### The authentication mechanism is vulnerable to SQL Injection, allowing an attacker to bypass login controls and gain access without valid credentials.

<img width="685" height="657" alt="Image" src="https://github.com/user-attachments/assets/5cb05dcd-9784-442f-9b6f-0f60c4999773" />
<img width="1076" height="542" alt="Image" src="https://github.com/user-attachments/assets/10ef0b10-8fa3-4908-9450-bb4c89c63400" />
<img width="1562" height="705" alt="Image" src="https://github.com/user-attachments/assets/99fc0f09-a8cd-4052-b471-ab019a6e23cf" />
<img width="1156" height="693" alt="Image" src="https://github.com/user-attachments/assets/befccf1f-9abb-431f-8e59-242c3e086d25" />
<img width="1156" height="693" alt="Image" src="https://github.com/user-attachments/assets/db3e5ad4-e728-47e8-8d9a-15621e4aadc7" />
<img width="1572" height="767" alt="Image" src="https://github.com/user-attachments/assets/7a339b9b-04e2-4c6c-bc1d-4de6f7a0d486" />
<img width="611" height="570" alt="Image" src="https://github.com/user-attachments/assets/cd2bcbf2-bcd6-48e2-a215-1f8a331b7064" />
<img width="512" height="746" alt="Image" src="https://github.com/user-attachments/assets/77fde89d-9423-4522-b7d1-2522cb29c588" />


### 8. SQL Injection 

#### The search endpoint is vulnerable to SQL Injection. By gradually modifying the search parameter in Burp Repeater, it was possible to trigger SQLite error messages and eventually enumerate all database tables.

Steps:

- Searched for the keyword “apple” in the search bar.
- Captured the request and sent it to Burp Repeater.
- Gradually modified the search parameter by adding special characters (', )), --).
- Observed SQLite error messages, confirming SQL Injection and revealing the backend database technology.
- Continued modifying the payload to extract metadata from sqlite_master.
- Successfully enumerated all database tables.



<img width="1892" height="630" alt="Image" src="https://github.com/user-attachments/assets/0dc10e3d-6de8-4a18-8de0-f2a615bd8178" />

-

<img width="1333" height="535" alt="Image" src="https://github.com/user-attachments/assets/0bff77bc-a037-4af8-b87a-b2590385d23f" />

-

<img width="1542" height="685" alt="Image" src="https://github.com/user-attachments/assets/c066b7fa-076a-4d23-bc17-35bd664363f1" />

-

<img width="1593" height="687" alt="Image" src="https://github.com/user-attachments/assets/9a27d51f-5a41-436e-a9db-cc41a9cb5a91" />

-

<img width="1522" height="617" alt="Image" src="https://github.com/user-attachments/assets/3d1f5d5d-897e-4be6-a2c9-819a7db1158f" />

-

<img width="1522" height="673" alt="Image" src="https://github.com/user-attachments/assets/b1e529ac-369b-49c0-81c6-281b272852e6" />

-

<img width="1522" height="626" alt="Image" src="https://github.com/user-attachments/assets/9fadfea5-6fd2-48b3-be60-70bc878a635f" />

-

<img width="1522" height="592" alt="Image" src="https://github.com/user-attachments/assets/71518071-4b61-4bde-adf8-f2bf70b4f985" />

-

<img width="1161" height="675" alt="Image" src="https://github.com/user-attachments/assets/62baee4f-d693-4fbd-9475-1ff2af01cf5c" />

-

<img width="1538" height="703" alt="Image" src="https://github.com/user-attachments/assets/cf4ea980-7900-4ded-9e5f-fb53396e987f" />

-

<img width="1358" height="671" alt="Image" src="https://github.com/user-attachments/assets/2092f689-1044-4cc7-8c55-0a5df3c69222" />


### 9. Cross-Site Scripting (XSS)

#### The search functionality is vulnerable to DOM‑based XSS. By injecting HTML/JavaScript into the search parameter, it was possible to execute arbitrary code, extract the authentication token, and decode sensitive user information.

Steps:

- Searched for “apple” and “banana”  both returned normal results.
- Searched for “robes”  received “no result found.”
- Searched for <iframe>  a small empty pop‑up window appeared, confirming HTML injection.
- Injected a crafted payload  the application executed it and displayed my IP address, proving DOM‑based XSS:
<img width="270" height="35" alt="Image" src="https://github.com/user-attachments/assets/22f1b08e-bb4e-4506-bb44-2a64f91bc63a" />


  
- Enhanced the payload  to extract the authentication token from the client:
<img width="485" height="35" alt="Image" src="https://github.com/user-attachments/assets/ebaa7c32-c60c-4cd4-90ff-a2a0b82a64b3" />
  
- Used Burp Suite Decoder to decode the token.
- Successfully viewed sensitive user information inside the token, including: User name, Email, Password hash and User role.


<img width="1712" height="547" alt="Image" src="https://github.com/user-attachments/assets/010c2ace-50a2-45f3-aa87-6dc6088009b2" />


<img width="1702" height="593" alt="Image" src="https://github.com/user-attachments/assets/25e1489e-1384-4518-851a-079a7d5a89ea" />


<img width="1651" height="757" alt="Image" src="https://github.com/user-attachments/assets/f7fa4e9b-7021-483f-bd5b-17a96be2ee6c" />


<img width="1652" height="802" alt="Image" src="https://github.com/user-attachments/assets/9bb15288-3ad6-4802-951a-972f92d59afe" />


<img width="1622" height="786" alt="Image" src="https://github.com/user-attachments/assets/4bae3beb-7d51-48b2-9705-fb070c98e552" />


<img width="1578" height="787" alt="Image" src="https://github.com/user-attachments/assets/649c06aa-6061-4fe7-a77a-1e1c6653bac3" />


<img width="1593" height="492" alt="Image" src="https://github.com/user-attachments/assets/d738512d-fd6a-4da8-9f4b-5b2bc6232d0b" />



## Phase 6 – Post‑Exploitation Analysis

#### Objectives


- Determine the extent of access, data exposure, and privilege escalation opportunities.

- Evaluate how an attacker could leverage compromised assets to deepen their foothold.

#### Potential Impacts
- Unauthorized administrative access:  
Compromised tokens, sessions, or credentials may allow attackers to escalate privileges and gain full administrative control.

- Sensitive data exposure:  
Access to user profiles, emails, password hashes, roles, and internal documents increases the risk of data breaches.

- Financial fraud:  
Manipulation of business logic, transactions, or user accounts could result in unauthorized purchases or financial loss.

- Account compromise:  
Extracted tokens or credentials can be used to impersonate users, take over accounts, or perform malicious actions.

- Loss of data integrity:  
Attackers may alter, delete, or corrupt data, impacting operational reliability and trust.

- Potential lateral movement opportunities:  
Access to internal tokens, APIs, or backend services may allow pivoting deeper into the environment.


## Phase 7 – Reporting
In alignment with NIST SP 800‑115, the Reporting phase consolidates all assessment activities, findings, evidence, and recommendations into a formal deliverable. This documentation provides a comprehensive record of the testing process and validated results. The complete penetration testing report is included in the accompanying report file.




## Tools Used
- Network & Enumeration: Nmap, Gobuster 
 
- Web Application Security: Burp Suite, OWASP Juice Shop, Browser DevTools 

- Infrastructure Analysis:
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

