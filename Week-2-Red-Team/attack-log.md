# SecureCorp Security Assessment
## Week 2 – Authorized Testing Log

### Scope
- Attacker: Kali Linux (10.10.10.5)
- Target: Metasploitable2 (10.10.10.10)
- Network: VirtualBox Internal Network (intnet)

### Authorization and Safety
- Testing is restricted to the isolated lab target.
- No public, campus, home, or third-party systems are in scope.
- Testing will stop if the target or network scope is uncertain.

### Test Log

| Test ID | Activity | Status | Evidence |
|---|---|---|---|
| T01 | Initial Nmap service/version scan | Completed | Week-1-Lab-Setup/nmap-scan.txt |
| T02 | Review discovered services | Completed | application-map.md |
| T03 | Further authorized service assessment | Pending | To be recorded |
| T04 | Web application security assessment | Pending | To be recorded |
| T05 | Review relevant security logs | Pending | To be recorded |

### Results
The initial scan identified multiple reachable services. This establishes the current service inventory but does not, by itself, confirm exploitable vulnerabilities.

### Evidence Recording
For each future test, record:
- Date and time
- Test objective and command or method
- Target IP and service
- Actual result
- Evidence filename or screenshot
- Limitations and cleanup performed

### Current Limitations
No exploitation result or successful shell access is claimed in this log.

### Overall Status
Initial reconnaissance completed. Further testing is pending.
