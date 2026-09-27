# Analyst Report — Case-006  
  
## Case Information  
  
**Case:** Scheduled Task Persistence Investigation    
**Endpoint:** SOC-WIN10    
**SIEM:** Wazuh    
**Status:** Closed    
**Disposition:** Authorized Security Simulation  
  
## Investigation  
  
A scheduled task named `SOC-Case006-Test` was identified on the endpoint.  
  
The task was configured to execute:  
  
`C:\Users\SOC_Lab\AppData\Local\Temp\case006.cmd`  
  
Task inspection confirmed the task was enabled and had successfully executed.  
  
Wazuh/Sysmon telemetry showed:  
  
`svchost.exe → cmd.exe → case006.cmd`  
  
The parent process was associated with the Windows Task Scheduler service:  
  
`svchost.exe -k netsvcs -p -s Schedule`  
  
Wazuh generated:  
  
- **Rule:** 92052  
- **Level:** 4  
- **MITRE:** T1059.003 — Windows Command Shell  
  
Analyst review additionally identified the scheduled-task behavior as consistent with:  
  
**T1053.005 — Scheduled Task/Job: Scheduled Task**  
  
## Analysis  
  
Scheduled tasks are legitimate Windows functionality but can also be abused to establish persistence or execute commands.  
  
Correlation between endpoint task configuration and Wazuh process telemetry confirmed that the scheduled task executed the configured command file.  
  
The activity was part of an authorized SOC lab simulation and no malicious payload was involved.  
  
## Remediation  
  
The scheduled task was deleted and a subsequent query confirmed it no longer existed.  
  
Associated files were removed:  
  
- `case006.cmd`  
- `case006-result.txt`  
  
`Test-Path` returned `False` for both artifacts, confirming cleanup.  
  
## Final Disposition  
  
**Authorized Security Simulation — Remediated**  
  
No escalation required.  
