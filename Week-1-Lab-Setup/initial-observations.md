# Initial Network Observations

## Target Information
- Target IP: 10.10.10.10
- Target hostname: metasploitable.localdomain
- Target status: Up
- Scan tool: Nmap 7.99
- Scan type: Service and version detection (-sV)
- Total open TCP ports observed: 22

## Key Observations
1. FTP service detected on port 21.
2. SSH service detected on port 22.
3. Telnet service detected on port 23.
4. HTTP service detected on port 80.
5. SMB services detected on ports 139 and 445.
6. A bindshell service was detected on port 1524.
7. Database services were detected on ports 3306 and 5432.
8. Additional services include IRC, VNC, NFS, and Tomcat.

## Preliminary Security Concerns
- Multiple exposed services increase the attack surface.
- Telnet and other legacy services require configuration review.
- Service versions should be checked against reliable vulnerability references.
- Access controls and unnecessary services should be reviewed.

## Limitations
- This scan identifies services and reported versions only.
- Vulnerabilities have not all been independently verified.
- Wazuh log collection is not yet configured.

## Evidence
- Raw scan output: nmap-scan.txt
