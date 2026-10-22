# SecureCorp Security Assessment

## 1. Executive Summary

This project documents a cybersecurity assessment conducted in an isolated virtual lab using Kali Linux and Metasploitable2.

The assessment focused on network reconnaissance, service identification, HTTP security observations, and basic security log monitoring.

The purpose was to identify observable security weaknesses, collect supporting evidence, and recommend practical remediation measures.

## 2. Scope and Environment

### Lab Environment
- Attacker and assessment system: Kali Linux
- Target system: Metasploitable2
- Kali lab IP: 10.10.10.5
- Target lab IP: 10.10.10.10
- Network: Isolated VirtualBox lab

### Scope
The assessment included:
- Lab network connectivity verification
- Nmap service discovery
- HTTP response-header inspection
- WebDAV configuration inspection
- Authentication-log review
- Investigation of remote syslog forwarding

All testing was conducted against the designated lab environment.

## 3. Assessment Methodology

The assessment followed these stages:

1. Lab setup and connectivity verification
2. Network and service reconnaissance
3. HTTP and WebDAV configuration inspection
4. Authentication-log analysis
5. Evidence documentation
6. Findings and remediation recommendations

## 4. Findings

### Finding 1: Legacy Service and Software Versions

**Observation:** The target returned an HTTP response identifying Apache 2.2.8 and PHP 5.2.4.

**Potential Risk:** Legacy software versions may contain known vulnerabilities if they are unpatched and exposed to relevant attack paths.

**Severity:** Medium — preliminary assessment; requires vulnerability verification.

**Evidence:** `Week-2-Red-Team/evidence/http-headers.txt`

**Recommendation:**
- Upgrade unsupported software.
- Apply security patches.
- Disable unnecessary services.
- Restrict network access to required services.

### Finding 2: HTTP Server Information Disclosure

**Observation:** The HTTP response exposed server and PHP version information through response headers.

**Potential Risk:** Version disclosure can help an attacker identify software to investigate for known vulnerabilities. Version disclosure alone does not prove that the server is exploitable.

**Severity:** Low — preliminary assessment.

**Evidence:** `Week-2-Red-Team/evidence/http-headers.txt`

**Recommendation:**
- Minimize unnecessary server-version disclosure.
- Keep server software updated.
- Review HTTP response headers and server configuration.

### Finding 3: WebDAV Service Exposure

**Observation:** WebDAV-related HTTP capabilities were investigated during reconnaissance.

**Potential Risk:** Insecure WebDAV permissions or unnecessary write access may allow unauthorized file operations.

**Severity:** Requires further verification.

**Evidence:**
- `Week-2-Red-Team/evidence/webdav-options.txt`
- `Week-2-Red-Team/evidence/webdav-propfind.txt`
- `Week-2-Red-Team/evidence/webdav-directory.html`
- `Week-2-Red-Team/evidence/webdav-get-headers.txt`
- `Week-2-Red-Team/evidence/E06-webdav-options.png`



**Recommendation:**
- Disable WebDAV if it is not required.
- Restrict access to authorized users.
- Disable unnecessary write methods.
- Review permissions and access logs.

### Finding 4: Centralized Syslog Forwarding Not Verified

**Observation:** Test messages were recorded in the target's local syslog. Kali was configured to receive UDP syslog messages, but successful delivery and storage of the target's syslog messages on Kali could not be confirmed.

**Potential Risk:** Without verified centralized logging, security events may be harder to correlate and investigate across systems.

**Severity:** Monitoring gap — further validation required.

**Evidence:** `Week-3-Blue-Team/evidence/kali-auth-monitoring.txt`

**Recommendation:**
- Troubleshoot and verify remote log forwarding.
- Confirm that messages arrive at the monitoring system.
- Protect logs against unauthorized modification.
- Establish log retention and review procedures.
### Finding 5: Root-Shell Prompt Observed on TCP Port 1524

**Observation:** A Netcat connection to the Metasploitable2 target (`10.10.10.10`) on TCP port `1524` displayed the prompt `root@metasploitable:/#`.

**Assessment:** This observation indicates that the connection reached a root-shell prompt. However, no additional commands were executed, so command execution was not independently verified.

**Potential Impact:** If the service is accessible to an unauthorized user, it could expose the target system to severe compromise.

**Severity:** Critical potential impact; validation and service configuration review required.

**Evidence:** `Week-2-Red-Team/evidence/E07-port-1524-root-shell.txt`

**Recommended Controls:**

* **Technical:** Disable the bind-shell service if it is not required and restrict access to necessary services.
* **Compensating:** Isolate the vulnerable lab system and restrict network access to trusted lab machines.
* **Detective:** Monitor for unexpected connections to TCP port 1524 and investigate related network and system logs.


## 5. Blue Team Monitoring

Kali Linux authentication logs were reviewed to examine recorded administrative commands and session events.

The collected evidence contains sudo command and session records.

No failed-login event was confirmed in the reviewed output. This does not establish that no failed logins occurred elsewhere or at other times.

## 6. Limitations

- Testing was performed in an isolated educational lab.
- The assessment was not a complete penetration test.
- Findings require additional validation before being treated as confirmed exploitable vulnerabilities.
- Remote syslog forwarding remains unverified.
- The report does not claim that every service or security weakness on the target was identified.

## 7. Remediation Priorities

1. Upgrade unsupported software and apply security updates.
2. Review exposed services and disable unnecessary services.
3. Verify WebDAV permissions and restrict access.
4. Complete and validate centralized logging.
5. Establish regular log review and evidence-retention procedures.

## 8. Conclusion

The SecureCorp Security Assessment project provided practical experience with network reconnaissance, HTTP configuration review, evidence collection, and authentication-log analysis.

The assessment identified areas requiring further security review, including legacy software, server information disclosure, WebDAV configuration, and centralized logging.

Recommended next steps are to validate the findings, remediate confirmed weaknesses, and verify that monitoring controls operate as intended.

## 9. Evidence Index

- Week 2 reconnaissance evidence: `Week-2-Red-Team/evidence/`
- Week 3 authentication monitoring evidence: `Week-3-Blue-Team/evidence/kali-auth-monitoring.txt`

## 10. Assessment Status

**Project:** SecureCorp Security Assessment
**Environment:** Isolated VirtualBox lab
**Status:** Initial assessment documented; further validation and remediation verification recommended.
