# SQL Injection – Payroll Application Lab

## Overview
This project demonstrates the exploitation of a SQL Injection vulnerability
in a deliberately vulnerable payroll web application within a controlled lab
environment.

The goal of this lab was to identify an injectable parameter, exploit it,
and extract sensitive data from the backend database.

## Environment
- Attacker: Kali Linux
- Target: Vulnerable Payroll Web Application
- Web Server: Apache (PHP)
- Database: MySQL

## Tools Used
- Nmap
- SQLMap
- Metasploit Framework (initial service enumeration)
- Kali Linux

## Vulnerability Identified
- SQL Injection via POST parameter `user`
- Injection Type: UNION-based and Time-based blind
- Affected DBMS: MySQL

## Exploitation Steps
1. Performed service and port scanning using Nmap
2. Identified web application running on port 80
3. Discovered login form on payroll_app.php
4. Used SQLMap to test POST parameters
5. Confirmed SQL Injection on `user` parameter
6. Enumerated available databases
7. Dumped contents of `payroll.users` table

## Impact
- Unauthorized access to employee records
- Exposure of usernames, plaintext passwords, and salary information
- Complete compromise of the payroll database

## Mitigation Recommendations
- Use prepared statements (parameterized queries)
- Implement strict input validation and sanitization
- Enforce least privilege for database users
- Avoid storing plaintext passwords (use hashing)

## Disclaimer
This project was conducted in a controlled lab environment strictly for
educational and ethical hacking purposes. Unauthorized testing on live
systems is illegal.
