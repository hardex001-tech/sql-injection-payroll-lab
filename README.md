# SQL Injection Payroll Lab

## 1. Project Overview
This lab demonstrates a **SQL Injection vulnerability** in a simulated payroll web application.  
The objective is to show how improper input validation can lead to full database compromise.

⚠️ This project was performed in a controlled lab environment for educational purposes only.

---

## 2. Scope & Objectives
- Perform network and service enumeration
- Identify a vulnerable web application
- Detect and exploit a SQL Injection flaw
- Extract sensitive data from the backend database
- Document impact and remediation steps

---

## 3. Environment & Tools
**Operating System**
- Kali Linux

**Tools Used**
- Nmap – service and port enumeration
- SQLMap – automated SQL Injection exploitation
- Web Browser – manual interaction and verification

---

## 4. Enumeration
Initial reconnaissance was performed against the target host to identify exposed services.

- Open port **80 (HTTP)** discovered
- Web application identified on the HTTP service
- Login interface found at `payroll_app.php`

**Command used:**
```bash
nmap -sC -sV -p- TARGET_IP
5. Vulnerability Discovery
The login form was tested for input validation weaknesses.

POST parameter user identified as injectable

SQL Injection confirmed

Backend DBMS identified as MySQL

Command used:

sqlmap -u "http://TARGET_IP/payroll_app.php" --forms --batch
6. Exploitation
Once SQL Injection was confirmed, database enumeration and data extraction were performed.

Enumerate databases:

sqlmap -u "http://TARGET_IP/payroll_app.php" --dbs
Enumerate and dump users table:

sqlmap -u "http://TARGET_IP/payroll_app.php" -D payroll -T users --dump
Extracted data included:

Usernames

Passwords

Employee salary information

7. Impact Assessment
This vulnerability enables:

Full database compromise

Exposure of sensitive employee data

Potential privilege escalation

Risk of further internal system abuse

8. Defensive Recommendations
To mitigate this vulnerability:

Use prepared statements (parameterized queries)

Enforce strict server-side input validation

Apply least-privilege principles to database accounts

Hash and salt passwords using strong algorithms (e.g., bcrypt)

Implement proper error handling to prevent information leakage

Disclaimer
This project was conducted strictly in a legal lab environment.
Unauthorized testing of systems without permission is illegal and unethical.

Author
hardex001-tech
Cybersecurity / Ethical Hacking Lab


