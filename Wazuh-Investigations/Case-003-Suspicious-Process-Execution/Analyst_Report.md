# Analyst Report — Wazuh Case 003

## Case Information

**Case ID:** WAZUH-003  
**Endpoint:** SOC-WIN10  
**Alert Source:** Wazuh / Sysmon  
**Event Type:** Process Creation  
**Event ID:** 1  
**Classification:** Benign True Positive

## Alert Summary

Wazuh detected PowerShell spawning a Windows Command Shell on the SOC-WIN10 endpoint.

Sysmon telemetry confirmed that `powershell.exe` launched `cmd.exe`, which executed the `net user` command.

## Technical Findings

- **Process:** `C:\Windows\System32\cmd.exe`
- **Parent Process:** `C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe`
- **Command Line:** `cmd.exe /c "net user"`
- **User:** SOC_Lab
- **Integrity Level:** High
- **Wazuh Rule ID:** 92004
- **Rule Level:** 4
- **Rule Description:** Powershell process spawned Windows command shell instance

## MITRE ATT&CK

- **Technique ID:** T1059.003
- **Technique:** Windows Command Shell
- **Tactic:** Execution

## Analysis

The process chain was identified as:

`powershell.exe → cmd.exe → net user`

The `net user` command was used to enumerate Windows user accounts.

Wazuh correctly identified PowerShell spawning a Windows Command Shell. Review of the available telemetry did not identify additional evidence of malware execution, persistence, credential theft, privilege escalation, or malicious downloads.

The activity was intentionally generated as part of an authorized SOC training exercise.

## Analyst Verdict

**Benign True Positive**

The detection accurately identified the process execution behavior. However, the activity was authorized and no additional malicious indicators were identified.

## Recommended Action

No escalation is required.

Document the activity as authorized lab behavior and close the alert as a Benign True Positive.

## Evidence Reviewed

- Windows command execution
- Sysmon Event ID 1 process telemetry
- Parent-child process relationship
- Wazuh Rule 92004
- MITRE ATT&CK T1059.003 mapping