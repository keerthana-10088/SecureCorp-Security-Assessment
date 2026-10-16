# SecureCorp Security Assessment
## Week 2 – Authorized Testing Log

### Scope
- Attacker: Kali Linux (10.10.10.5)
- Target: Metasploitable2 (10.10.10.10)
- Network: VirtualBox Internal Network (`intnet`)

### Authorization and Safety
- Testing is restricted to the isolated lab target.
- No public, campus, home, or third-party systems are in scope.
- Testing will stop if the target or network scope is uncertain.
- Activities documented here are limited to the tests and evidence described below.

### Test Log

| Test ID | Activity | Status | Evidence |
|---|---|---|---|
| T01 | Initial Nmap service/version scan | Completed | `../Week-1-Lab-Setup/nmap-scan.txt` |
| T02 | Review discovered services | Completed | `application-map.md`; `metasploitable-scan.txt` |
| T03 | FTP anonymous access verification | Completed | `metasploitable-scan.txt`; manual FTP session |
| T04 | Non-invasive web application review | Completed (limited) | `evidence/webdav-options.txt`; `evidence/webdav-propfind.txt`; `evidence/webdav-directory.html`; `evidence/dvwa-login-review.txt` |
| T05 | Read-only security log review | Completed (limited) | Target log review notes; see Security Log Review below |

### Results Summary

The initial service scan identified multiple reachable services on the lab target. Additional read-only checks reviewed FTP anonymous access, HTTP response headers, WebDAV responses, the DVWA login page, and selected security logs.

The observations documented below indicate areas that require configuration review. They do not, by themselves, establish that every observed service is exploitable.

### WebDAV Reconnaissance Finding

- **Target:** `10.10.10.10:80/dav/`
- **Service reported:** Apache/2.2.8 (Ubuntu), DAV/2
- **Test:** An HTTP OPTIONS request was used to identify advertised methods.
- **Result:** The server advertised DELETE, TRACE, PROPFIND, PROPPATCH, COPY, MOVE, LOCK, and UNLOCK among its allowed methods.
- **PROPFIND result:** The request returned HTTP 207 Multi-Status. The response described the `/dav/` collection but did not list files or subdirectories.
- **Directory listing:** A GET request returned HTTP 200 and displayed an "Index of /dav" page containing only the Parent Directory entry.
- **Assessment:** WebDAV methods and directory indexing were observed. Review whether WebDAV is required and verify access controls. Unauthorized modification or deletion has not been demonstrated.
- **Evidence:** `evidence/webdav-options.txt`; `evidence/webdav-propfind.txt`; `evidence/webdav-directory.html`; `evidence/webdav-get-headers.txt`
- **Limitations:** No files were created, modified, or deleted during these checks.

### DVWA Login Page Review

- **Target:** `10.10.10.10:80/dvwa/`
- **Result:** `/dvwa/` returned HTTP 302 and redirected to `login.php`; the login page returned HTTP 200.
- **Form:** POST to `login.php`, with `username` and `password` fields.
- **Server disclosure:** Apache/2.2.8 (Ubuntu) and PHP/5.2.4-2ubuntu5.10 were reported.
- **Headers and cookies:** Common browser security headers were not present in the captured response. The PHPSESSID cookie did not show Secure, HttpOnly, or SameSite attributes in the reviewed evidence.
- **Assessment:** Review the web server's security-header and session-cookie configuration. These observations do not independently prove exploitability.
- **Evidence:** `evidence/dvwa-login-review.txt`
- **Limitations:** No credentials were submitted; no login bypass or exploitation was attempted.

### FTP Anonymous Access Finding

- **Target:** `10.10.10.10:21`
- **Service reported:** vsftpd 2.3.4
- **Test:** Connected using the FTP username `anonymous`.
- **Result:** The server returned `230 Login successful`.
- **Directory listing:** The `ls` command completed, but no filenames were displayed in the recorded session.
- **Assessment:** Anonymous FTP login was accepted. The contents accessible through this session were not established. Review whether anonymous access is required and restrict it if unnecessary.
- **Evidence:** `metasploitable-scan.txt`; manual FTP session notes
- **Limitations:** No files were downloaded, modified, or deleted.

### HTTP Security Headers Review

- **Target:** `10.10.10.10:80`
- **Test:** Reviewed the captured HTTP response headers.
- **Result:** The response returned HTTP 200 OK and disclosed Apache/2.2.8 (Ubuntu) and PHP/5.2.4-2ubuntu5.10.
- **Observation:** Common security headers such as Content-Security-Policy, X-Frame-Options, and X-Content-Type-Options were not present in the captured response.
- **Assessment:** Review the server and application configuration to determine which security headers are appropriate. A single captured response does not establish that the headers are absent across the entire application.
- **Evidence:** `evidence/http-headers.txt`; `evidence/E05-http-headers.png`
- **Limitations:** This was a read-only review; no configuration changes were made.

### Security Log Review

- **Target:** Metasploitable2 (`10.10.10.10`)
- **Test:** Read-only review of `/var/log/syslog` and `/var/log/auth.log`.
- **Result:** The reviewed system logs contained DHCP/network messages, scheduled CRON session events, and kernel resume-from-disk errors.
- **Authentication review:** The commands used to search the reviewed entries did not return matching failed-login patterns.
- **Assessment:** No suspicious login activity was confirmed from the limited log entries reviewed. This does not prove that failed-login attempts never occurred.
- **Limitations:** Only selected log files and recent entries were reviewed. No log files were modified.
- **Centralized logging:** Remote syslog forwarding from Metasploitable2 to Kali remains unverified and must not be treated as successfully configured.

### Evidence Recording

For future tests, record:
- Date and time
- Test objective and command or method
- Target IP and service
- Actual result
- Evidence filename or screenshot
- Limitations and cleanup performed

### Current Limitations

- No successful exploitation or shell access is claimed in this log.
- The assessment is limited to the tests and evidence documented here.
- Old software versions and exposed service methods require further validation before assigning confirmed vulnerability status.
- Centralized remote syslog delivery has not been verified.
- Findings should be reviewed alongside their original evidence files.

### Overall Status

Initial reconnaissance, FTP anonymous-login verification, limited non-invasive web application review, HTTP response-header review, and a read-only review of selected security logs are documented.

The reviewed observations identify configuration areas for further investigation. Centralized remote syslog forwarding remains unverified, and no successful exploitation is claimed.
