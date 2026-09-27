# Analyst Report — Case-005  
  
## Case Information  
  
**Case:** Certutil Decode Investigation    
**Endpoint:** SOC-WIN10    
**SIEM:** Wazuh    
**Source:** Sysmon Event ID 1    
**Date:** September 23, 2026    
**Status:** Closed    
**Disposition:** Benign True Positive  
  
## Alert  
  
Wazuh detected PowerShell executing `certutil.exe` to decode a file.  
  
- **Rule ID:** 92073  
- **Level:** 6  
- **MITRE ATT&CK:** T1140  
- **Tactic:** Defense Evasion  
- **Technique:** Deobfuscate/Decode Files or Information  
  
## Investigation  
  
The detected process was:  
  
`C:\Windows\System32\certutil.exe`  
  
Command line:  
  
`certutil.exe -decode ...\soc-case005.b64 ...\soc-case005-decoded.txt`  
  
Process telemetry established the following relationship:  
  
`powershell.exe → certutil.exe`  
  
The process executed as `SOC_Lab` with Medium integrity.  
  
The SHA-256 of `certutil.exe` was checked using VirusTotal and returned **0/70 detections**.  
  
The decoded artifact was then inspected and contained:  
  
`SOC Case 005 - Safe Training File`  
  
SHA-256 of decoded file:  
  
`365F7EB0B822FC9D3BD8709A1D81958AEC2B1C3C880D2B93D70C234BE15B21CE`  
  
## Analysis  
  
`certutil.exe` is a legitimate Windows utility, but its decoding functionality can also be abused to decode or deobfuscate malicious content.  
  
The command therefore warranted investigation despite the legitimate executable reputation.  
  
Analysis of the process chain, executable reputation, and decoded artifact found no evidence of malicious payload execution or additional suspicious activity.  
  
## Final Disposition  
  
**Benign True Positive**  
  
Wazuh correctly detected behavior associated with T1140, but the decoded content was confirmed to be harmless.  
  
**Action:** Closed — no escalation required.  
  
## Analyst Takeaway  
  
Legitimate Windows utilities can generate security alerts when used in ways that overlap with attacker techniques. Analysts should investigate the command context and resulting artifacts rather than relying only on the reputation of the executable.  
