# SecureCorp Security Assessment
## Week 1 – CIA Analysis

### 1. Confidentiality
Objective: Protect sensitive information from unauthorized access.

Potential risks:
- Unauthorized access through exposed network services.
- Weak authentication on remote-access services.
- Sensitive information exposure through misconfigured services.

Recommended controls:
- Use strong passwords and secure authentication.
- Disable unnecessary services.
- Restrict access to sensitive data.

### 2. Integrity
Objective: Prevent unauthorized modification of data.

Potential risks:
- Unauthorized changes to files or system configurations.
- Compromised services allowing unwanted modifications.

Recommended controls:
- Apply appropriate file permissions.
- Maintain backups.
- Monitor important file and configuration changes.

### 3. Availability
Objective: Ensure authorized users can access systems when needed.

Potential risks:
- Service disruption caused by attacks or misconfiguration.
- Resource exhaustion.
- Failure of critical services.

Recommended controls:
- Monitor service availability.
- Maintain backups and recovery procedures.
- Keep systems maintained and securely configured.

## Initial Assessment
The Nmap scan identified multiple exposed services on the Metasploitable2 lab target. These services require further assessment to determine their actual security impact.

Note: These are preliminary risks, not confirmed security incidents.
