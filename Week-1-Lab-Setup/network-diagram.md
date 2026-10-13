# SecureCorp Security Assessment - Network Diagram

```text
             Isolated VirtualBox Network
                    Name: intnet
                  Network: 10.10.10.0/24

       +--------------------+
       |     Kali Linux     |
       |  Testing Machine   |
       |    10.10.10.5     |
       +--------------------+
                 |
                 |
  +--------------+------------------+
  |                                 |
  |                                 |
+----------------------+   +----------------------+
|    Metasploitable2   |   | Ubuntu Server +      |
|   Vulnerable Target  |   | Wazuh Monitoring     |
|     10.10.10.10      |   | 10.10.10.20 (planned)|
+----------------------+   +----------------------+

Note: Ubuntu/Wazuh installation and logging integration are pending.
All machines should use the isolated Internal Network intnet.
