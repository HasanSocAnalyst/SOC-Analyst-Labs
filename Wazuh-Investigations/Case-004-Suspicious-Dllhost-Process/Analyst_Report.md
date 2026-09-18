# Analyst Report — Case-004  
  
## Case Information  
  
**Case:** Suspicious dllhost.exe Investigation    
**Endpoint:** SOC-WIN10    
**SIEM:** Wazuh    
**Source:** Sysmon Event ID 1    
**Date:** September 18, 2026    
**Status:** Closed    
**Disposition:** Benign True Positive  
  
## Alert  
  
Wazuh generated a Level 12 alert for suspicious `dllhost.exe` execution.  
  
- **Rule ID:** 61638  
- **MITRE ATT&CK:** T1055 — Process Injection  
- **Process:** `dllhost.exe`  
  
## Investigation  
  
Sysmon recorded:  
  
`C:\Windows\System32\dllhost.exe`  
  
Command line:  
  
`C:\Windows\system32\DllHost.exe /Processid:{AB8902B4-09CA-4BB6-B78D-A8F59079A8D5}`  
  
The process was identified as Microsoft Windows COM Surrogate and executed from the expected System32 directory under `DESKTOP-H6J6VE5\SOC_Lab`.  
  
SHA-256:  
  
`0309834D40475CCD5A88C48F7FF5EC62E5C6798900357DD83665C3D0345124E0`  
  
VirusTotal analysis returned **0/70 detections** and identified the binary as Microsoft-distributed.  
  
## Telemetry Limitation  
  
Complete parent-process attribution was unavailable.  
  
Sysmon recorded an all-zero `ParentProcessGuid`, while `ParentImage`, `ParentCommandLine`, and `ParentUser` were unavailable.  
  
Because of this, no unsupported assumptions were made about the process ancestry.  
  
## Analysis  
  
The Level 12 alert and T1055 mapping warranted investigation but did not independently prove process injection.  
  
The expected executable location, Microsoft metadata, COM Surrogate command line, and clean hash reputation supported legitimate Windows activity.  
  
No additional evidence establishing malicious payload execution or process injection was identified.  
  
## Final Disposition  
  
**Benign True Positive**  
  
The activity matched Wazuh's detection logic, but the available evidence was consistent with legitimate Windows COM Surrogate activity.  
  
**Action:** Closed — no escalation required.  
  
## Analyst Takeaway  
  
High alert severity and MITRE ATT&CK mappings should guide investigation priority, not determine the final verdict. Process context and supporting evidence must be validated before escalation.  
