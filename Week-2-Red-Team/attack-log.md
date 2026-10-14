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
| T03 | FTP anonymous access verification | Completed | metasploitable-scan.txt; manual FTP session |
| T04 | Web application security assessment | Pending | To be recorded |
| T05 | Review relevant security logs | Pending | To be recorded |

### Results
The initial scan identified multiple reachable services. This establishes the current service inventory but does not, by itself, confirm exploitable vulnerabilities.

### WebDAV Reconnaissance Finding
- Target: 10.10.10.10:80/dav/
- Service: Apache/2.2.8 (Ubuntu), DAV/2
- Test: Sent an HTTP OPTIONS request to identify advertised methods.
- Result: The server advertised DELETE, TRACE, PROPFIND, PROPPATCH, COPY, MOVE, LOCK, and UNLOCK among its allowed methods.
- Verification: A PROPFIND request returned HTTP 207 Multi-Status. The response described the /dav/ collection but did not list files or subdirectories.
- Directory listing: A GET request returned HTTP 200 and displayed an "Index of /dav" page. Only the Parent Directory entry appeared.
- Assessment: WebDAV methods and directory indexing are enabled. Further review of access controls is required; unauthorized modification or deletion has not been demonstrated.
- Evidence: evidence/webdav-propfind.txt; evidence/webdav-directory.html; evidence/webdav-get-headers.txt
- Limitations: No files were created, modified, or deleted during these checks.

### FTP Anonymous Access Finding
- Target: 10.10.10.10:21
- Service: vsftpd 2.3.4
- Test: Connected using the FTP username `anonymous`.
- Result: Server returned `230 Login successful`.
- Directory listing: The `ls` command completed, but no filenames were displayed.
- Assessment: Anonymous FTP access is confirmed. The contents accessible through this session were not established.
- Limitations: No files were downloaded, modified, or deleted.

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
Initial reconnaissance and anonymous FTP access verification completed. Web application security assessment and log review are pending.
