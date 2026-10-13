# SecureCorp Security Assessment
## Week 1 – Preliminary Risk Assessment

| ID | Potential Risk | Evidence/Observation | Potential Impact | Priority | Recommended Action |
|---|---|---|---|---|---|
| R1 | Unnecessary services exposed | Nmap detected multiple open ports | Increased attack surface | High | Review and disable unnecessary services |
| R2 | Outdated service versions | Older versions reported by Nmap | Potential known vulnerabilities | High | Verify vulnerabilities and plan updates |
| R3 | Insecure remote access | Telnet and rsh-related services detected | Credentials or sessions may be exposed | High | Prefer encrypted alternatives and restrict access |
| R4 | Database services exposed | MySQL and PostgreSQL ports detected | Unauthorized data access if poorly secured | High | Restrict network access and review authentication |
| R5 | Web services require review | HTTP and Tomcat services detected | Possible web application weaknesses | Medium | Perform authorized configuration and application testing |

## Risk Assessment Notes

- This is a preliminary assessment based on the initial Nmap scan.
- Priorities are provisional and must be validated during further testing.
- An open port or old version alone does not prove a vulnerability.
- No successful exploitation is claimed in this document.
- Testing is restricted to the isolated VirtualBox lab.

## General Recommendations

1. Disable services that are not required.
2. Review software versions and available security updates.
3. Use secure authentication and encrypted remote access.
4. Restrict database and administrative services to trusted systems.
5. Record evidence and retest after remediation.
