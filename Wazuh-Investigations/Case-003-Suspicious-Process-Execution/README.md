# Wazuh Investigation — Case 003

## Case Summary

Wazuh detected PowerShell spawning a Windows Command Shell on the SOC-WIN10 endpoint.

Sysmon telemetry showed `powershell.exe` launching `cmd.exe`, which executed the `net user` command.

## Detection Details

- **Endpoint:** SOC-WIN10
- **Process:** `C:\Windows\System32\cmd.exe`
- **Parent Process:** `powershell.exe`
- **Command:** `cmd.exe /c "net user"`
- **User:** SOC_Lab
- **Sysmon Event ID:** 1
- **Wazuh Rule ID:** 92004
- **Rule Level:** 4

## MITRE ATT&CK

- **Technique:** Windows Command Shell
- **Technique ID:** T1059.003
- **Tactic:** Execution

## Investigation

The process chain observed was:

`powershell.exe → cmd.exe → net user`

The activity was reviewed to determine whether the command execution was associated with malicious behavior.

No additional evidence of malware, persistence, credential theft, privilege escalation, or malicious downloads was identified.

## Conclusion

**Classification: Benign True Positive**

Wazuh correctly detected PowerShell spawning `cmd.exe`. The activity was intentionally generated as part of an authorized SOC training lab and no additional malicious indicators were identified.

## Evidence

See the `evidence/` directory for supporting screenshots.