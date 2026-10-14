# SecureCorp Security Assessment
## Week 2 – Application and Service Map

### Objective
Document the services discovered on the authorized lab target.

### Target Information
- Target: Metasploitable2
- IP Address: 10.10.10.10
- Attacker Machine: Kali Linux
- Attacker IP: 10.10.10.5
- Environment: Isolated VirtualBox Internal Network

### Discovered Services
The initial Nmap service scan identified the following services:

| Port | Service | Detected Version |
|---|---|---|
| 21 | FTP | vsftpd 2.3.4 |
| 22 | SSH | OpenSSH 4.7p1 |
| 23 | Telnet | Version not confirmed |
| 25 | SMTP | Postfix |
| 53 | DNS | BIND 9.4.2 |
| 80 | HTTP | Apache 2.2.8 |
| 139/445 | SMB | Samba 3.X–4.X |
| 3306 | MySQL | 5.0.51a |
| 5432 | PostgreSQL | 8.3.0–8.3.7 |
| 5900 | VNC | Version not confirmed |
| 8180 | HTTP | Apache Tomcat |

### Initial Observations
- Multiple network services are reachable on the target.
- Several detected software versions are old.
- Telnet is an unencrypted remote-access protocol.
- Web, database, file-sharing, and remote-access services require further assessment.

### Limitations
- This map is based on the initial Nmap service/version scan.
- Service detection does not independently confirm an exploitable vulnerability.
- Additional ports and service details are available in the original scan file.

### Evidence
- Week-1 scan: ../Week-1-Lab-Setup/nmap-scan.txt

### Status
Initial service mapping completed. Further authorized testing is pending.


### Additional Web Application Observations

#### HTTP Service
- URL: http://10.10.10.10/
- HTTP response: `200 OK`
- Server header: Apache/2.2.8 (Ubuntu) DAV/2
- PHP header: PHP/5.2.4-2ubuntu5.10
- Assessment: Detected software versions are old and warrant further security review. Version headers alone do not prove exploitability.

#### Available Web Application Paths
The homepage HTML listed these paths:
- `/twiki/`
- `/phpMyAdmin/`
- `/mutillidae/`
- `/dvwa/`
- `/dav/`

These paths were observed in the homepage HTML. Their security has not yet been fully assessed.

#### DVWA Login Page
- Path: `/dvwa/`
- Initial response: `302 Found`
- Redirect destination: `login.php`
- Login page title: Damn Vulnerable Web App (DVWA) - Login
- Form method: `POST`
- Form action: `login.php`
- Observed form fields: `username` and `password`
- Result: The login page is accessible and its form structure was identified.
- Limitation: No authentication bypass or other login vulnerability has been confirmed.

### Updated Evidence
- Nmap scan: `metasploitable-scan.txt`
- FTP access observation: Manual FTP session recorded in `attack-log.md`
- HTTP headers and DVWA page: Observed using `curl` from Kali Linux

### Updated Status
Initial service mapping, anonymous FTP access verification, and basic web application reconnaissance completed. Further web application security assessment and log review remain pending.
