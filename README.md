# SecureCorp Security Assessment

## Project Overview
This project documents a controlled cybersecurity assessment conducted in an isolated VirtualBox lab. It covers asset identification, network reconnaissance, preliminary risk assessment, security monitoring, and remediation recommendations.

## Objectives
- Identify lab assets and exposed network services.
- Review service information and potential security risks.
- Practice authorized security testing in an isolated environment.
- Document Blue Team monitoring activities.
- Assess the status of centralized logging.
- Provide practical remediation recommendations.

## Lab Environment

| System | Role | IP Address |
|---|---|---|
| Kali Linux | Security testing and monitoring | 10.10.10.5 |
| Metasploitable2 | Authorized lab target | 10.10.10.10 |
| Ubuntu/Wazuh | Planned monitoring environment | 10.10.10.20 |

**Note:** Ubuntu/Wazuh is a planned component; its deployment and integration are not confirmed.

## Project Progress

### Week 1 – Lab Setup and Risk Assessment
- Lab asset inventory documented.
- Initial Nmap service scan recorded.
- CIA analysis and preliminary risk assessment documented.
- Logging and monitoring plan prepared.

### Week 2 – Authorized Security Testing
- Application and service reconnaissance documented.
- HTTP response headers reviewed.
- WebDAV-related responses investigated.
- Testing notes, evidence index, and screenshots collected.
- Findings require interpretation within the documented testing scope.

### Week 3 – Blue Team Monitoring
- Kali authentication-log review documented.
- Monitoring evidence collected and indexed.
- Centralized remote syslog forwarding remains unverified.

### Week 4 – Final Report
- Final security assessment report prepared.
- Preliminary findings, limitations, and remediation recommendations documented.
- Findings should be interpreted alongside the supporting evidence.

## Preliminary Observations
- HTTP response headers disclose server and software version information.
- WebDAV-related behavior was investigated and requires careful configuration review.
- Centralized logging from Metasploitable2 to Kali has not been confirmed.

These observations do not, by themselves, prove that a service is exploitable.

## Recommended Remediation
- Upgrade unsupported operating systems and outdated software.
- Disable unnecessary services and restrict administrative interfaces.
- Review WebDAV configuration and disable it if not required.
- Configure centralized logging and verify that remote events arrive successfully.
- Retain evidence and retest changes in the authorized lab.

## Tools and Technologies
- Kali Linux
- Nmap
- VirtualBox
- Metasploitable2
- Apache HTTP server inspection tools
- Linux authentication logs
- Wazuh (planned; deployment not confirmed)

## Safety and Scope
All testing is restricted to the authorized, isolated VirtualBox lab. No public, campus, or third-party systems are within scope.

## Disclaimer
This project is for authorized cybersecurity education and lab-based security assessment only.
