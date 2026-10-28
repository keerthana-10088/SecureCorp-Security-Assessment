# Week 3 – Blue Team Monitoring

## Objective
The objective of Week 3 is to review authentication logs and understand basic security monitoring activities in the SecureCorp lab environment.

## Lab Environment
- Attacker and monitoring system: Kali Linux
- Target system: Metasploitable2
- Network: Isolated VirtualBox lab
- Target IP: 10.10.10.10
- Kali lab IP: 10.10.10.5

## Activities Performed

### 1. Authentication Log Review
Reviewed Kali Linux authentication logs stored in `/var/log/auth.log`.

### 2. Sudo Activity Monitoring
Filtered authentication logs to identify sudo commands and session events.

### 3. Evidence Collection
Saved the collected log records to:

`evidence/kali-auth-monitoring.txt`

### 4. Remote Syslog Investigation
Configured and investigated remote syslog forwarding from Metasploitable2 to Kali Linux.

The target system recorded test messages locally. However, successful delivery and storage of these messages on Kali Linux could not be verified.

## Findings
- Kali Linux authentication logs contain sudo command and session records.
- The collected logs provide evidence of administrative activity.
- No failed-login event was confirmed in the reviewed output.
- Remote syslog forwarding remains unresolved.

## Limitations
This assessment used a controlled, isolated lab environment. The collected evidence reflects only the commands and log records reviewed during this exercise.

## Conclusion
Week 3 demonstrates basic authentication-log analysis and evidence collection. Remote syslog forwarding requires further troubleshooting before centralized logging can be considered operational.
## Additional Syslog Connectivity Test

A UDP connectivity test was performed from Metasploitable2 (10.10.10.10) to Kali Linux (10.10.10.5) on port 5514.

Result: One UDP packet was captured successfully using tcpdump.

Limitation: This confirms UDP packet delivery on port 5514 only. Standard syslog forwarding on port 514 and Wazuh centralized log ingestion remain unverified.

## Overall Status

Basic authentication-log review and UDP packet capture are documented. Centralized security monitoring remains pending until the syslog configuration and Wazuh log ingestion are verified.
