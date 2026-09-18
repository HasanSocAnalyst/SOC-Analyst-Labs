# Case-004: Suspicious dllhost.exe Investigation  
  
## Overview  
  
This investigation analyzes a Level 12 Wazuh alert involving `dllhost.exe` on the Windows endpoint `SOC-WIN10`.  
  
Wazuh mapped the activity to MITRE ATT&CK T1055 (Process Injection). The alert was investigated using Sysmon process telemetry, command-line analysis, process ancestry, and SHA-256 reputation analysis.  
  
## Alert Details  
  
- **Endpoint:** SOC-WIN10  
- **Wazuh Rule:** 61638  
- **Severity:** Level 12  
- **Alert:** Sysmon - Suspicious Process - dllhost.exe  
- **MITRE ATT&CK:** T1055 — Process Injection  
- **Sysmon Event ID:** 1  
  
## Investigation  
  
The detected process was:  
  
`C:\Windows\System32\dllhost.exe`  
  
Command line:  
  
`C:\Windows\system32\DllHost.exe /Processid:{AB8902B4-09CA-4BB6-B78D-A8F59079A8D5}`  
  
The executable was identified as Microsoft Windows COM Surrogate and executed from the expected Windows System32 directory.  
  
SHA-256:  
  
`0309834D40475CCD5A88C48F7FF5EC62E5C6798900357DD83665C3D0345124E0`  
  
VirusTotal returned **0/70 detections** and identified the file as Microsoft-distributed.  
  
Complete process ancestry could not be established because Sysmon did not provide `ParentImage`, `ParentCommandLine`, or `ParentUser`.  
  
No corroborating evidence of malicious process injection or payload execution was identified.  
  
## Final Disposition  
  
**Benign True Positive**  
  
Wazuh correctly detected activity matching its suspicious `dllhost.exe` rule, but investigation found the available evidence consistent with legitimate Windows COM Surrogate activity.  
  
**Action:** Alert closed. No escalation required.  
  
## Evidence  
  
- `01-wazuh-level12-alert.png`  
- `02-dllhost-process-details.png`  
- `03-missing-parent-telemetry.png`  
- `04-virustotal-hash-analysis.png`  
  
## Skills Demonstrated  
  
- Wazuh alert triage  
- Sysmon process analysis  
- MITRE ATT&CK interpretation  
- Hash reputation analysis  
- Threat intelligence enrichment  
- Alert disposition  
