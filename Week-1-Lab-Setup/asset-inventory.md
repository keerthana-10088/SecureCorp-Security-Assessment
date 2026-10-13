# SecureCorp Security Assessment
## Week 1 – Asset Inventory

### 1. Kali Linux – Attacker Machine
- IP Address: 10.10.10.5
- Role: Security testing and network scanning
- Network: VirtualBox Internal Network (intnet)

### 2. Metasploitable2 – Vulnerable Target
- IP Address: 10.10.10.10
- Role: Authorized security testing target
- Network: VirtualBox Internal Network (intnet)
- Status: Reachable from Kali Linux

### 3. Ubuntu/Wazuh – Monitoring Machine
- Planned IP Address: 10.10.10.20
- Role: Centralized log monitoring and security event analysis
- Status: Configuration and connectivity pending

## Initial Network Scan

- Tool: Nmap
- Command: nmap -sV 10.10.10.10
- Result: Target reachable; 22 TCP ports reported open.
- Evidence File: nmap-scan.txt

## Initial Observations

- Multiple network services are exposed on the target.
- Several services report older software versions.
- Further investigation is needed to confirm potential vulnerabilities.
- This scan alone does not confirm that the services are exploitable.
