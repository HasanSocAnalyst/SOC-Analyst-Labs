# Case-006: Scheduled Task Persistence Investigation  
  
## Overview  
  
Investigation of scheduled-task activity on `SOC-WIN10`, including process correlation, persistence analysis, remediation, and verification.  
  
## Key Findings  
  
A scheduled task named `SOC-Case006-Test` was configured to execute:  
  
`C:\Users\SOC_Lab\AppData\Local\Temp\case006.cmd`  
  
Wazuh captured execution originating from the Windows Task Scheduler service:  
  
`svchost.exe → cmd.exe → case006.cmd`  
  
Wazuh generated Rule 92052 and mapped the execution to:  
  
- **MITRE ATT&CK:** T1059.003  
- **Technique:** Windows Command Shell  
- **Level:** 4  
  
The scheduled-task behavior was additionally analyzed as:  
  
- **MITRE ATT&CK:** T1053.005  
- **Technique:** Scheduled Task/Job: Scheduled Task  
- **Tactic:** Persistence / Privilege Escalation  
  
## Disposition  
  
**Authorized Security Simulation**  
  
The activity was intentionally generated in the SOC lab to simulate scheduled-task persistence.  
  
The scheduled task was deleted and its associated artifacts were removed. Verification confirmed successful remediation.  
  
## Skills Demonstrated  
  
- Wazuh/Sysmon investigation  
- Multi-source event correlation  
- Process-chain analysis  
- Scheduled-task persistence analysis  
- MITRE ATT&CK mapping  
- Remediation and verification  
