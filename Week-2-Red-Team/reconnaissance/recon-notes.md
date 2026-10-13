# Reconnaissance Notes

## Objective
Record initial reconnaissance findings for the authorized lab target.

## Lab Scope
- Attacker: Kali Linux
- Attacker IP: 10.10.10.5
- Target: Metasploitable2
- Target IP: 10.10.10.10
- Network: VirtualBox Internal Network (intnet)

## Method
An Nmap service/version scan was performed against the lab target.

## Observations
- Multiple TCP services were detected as open.
- FTP, SSH, HTTP, SMB, database, and remote-access services were among those identified.
- The complete scan output is stored in Week-1-Lab-Setup/nmap-scan.txt.

## Limitations
- These observations describe detected services only.
- Vulnerabilities have not yet been confirmed.
- Further assessment and log correlation are pending.

## Status
Initial reconnaissance completed.
