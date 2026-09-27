# Case-005: Certutil Decode Investigation  
  
## Overview  
  
This investigation examines a Wazuh alert generated when PowerShell executed `certutil.exe` to decode a Base64 file on the Windows endpoint `SOC-WIN10`.  
  
Wazuh mapped the activity to MITRE ATT&CK T1140 — Deobfuscate/Decode Files or Information.  
  
## Alert Details  
  
- **Endpoint:** SOC-WIN10  
- **Wazuh Rule:** 92073  
- **Severity:** Level 6  
- **Process:** certutil.exe  
- **MITRE ATT&CK:** T1140  
- **Tactic:** Defense Evasion  
- **Sysmon Event ID:** 1  
  
## Investigation  
  
Wazuh recorded:  
  
`C:\Windows\System32\certutil.exe`  
  
Command:  
  
`certutil.exe -decode ...\soc-case005.b64 ...\soc-case005-decoded.txt`  
  
Process ancestry showed:  
  
`powershell.exe → certutil.exe`  
  
The executable ran from the expected Windows System32 directory. SHA-256 reputation analysis of `certutil.exe` returned **0/70 detections** on VirusTotal.  
  
The decoded file was examined and contained:  
  
`SOC Case 005 - Safe Training File`  
  
No malicious payload or additional suspicious activity was identified.  
  
## Final Disposition  
  
**Benign True Positive**  
  
Wazuh correctly detected potentially suspicious use of `certutil.exe`, but investigation determined that the decoded content was harmless.  
  
**Action:** Alert closed. No escalation required.  
  
## Evidence  
  
- `01-certutil-process-details.png`  
- `02-certutil-process-chain.png`  
- `03-wazuh-rule-mitre-mapping.png`  
- `04-virustotal-certutil.png`  
- `05-decoded-file-analysis.png`  
  
## Skills Demonstrated  
  
- Wazuh alert triage  
- Sysmon process analysis  
- Parent-child process analysis  
- LOLBin investigation  
- Hash reputation analysis  
- MITRE ATT&CK interpretation  
- Alert disposition  
