# WAZUH-001 — PowerShell Enumeration

## Objective

Investigate PowerShell-related activity detected by Wazuh on the Windows SOC endpoint and determine whether the activity represents malicious execution.

## Environment

- SIEM/EDR: Wazuh
- Endpoint: SOC-WIN10
- Operating System: Windows 10
- Telemetry: Sysmon
- Event Type: Process Creation
- Sysmon Event ID: 1

## Detection

Wazuh detected PowerShell-related process execution.

- Rule ID: 92066
- Rule Level: 4
- MITRE ATT&CK: T1059.001
- Tactic: Execution
- Technique: PowerShell

## Investigation

PowerShell enumeration commands were executed on the endpoint.

Wazuh telemetry showed PowerShell spawning:

`C:\Windows\SysWOW64\SecEdit.exe`

The associated process chain and command-line activity were reviewed through Wazuh Threat Hunting.

The activity was determined to be associated with authorized system enumeration performed during the investigation lab.

## Classification

**Benign True Positive**

Wazuh correctly detected the activity, but the process execution was legitimate and no evidence of malicious activity was identified.

## Evidence

Screenshots documenting:

- PowerShell execution
- Wazuh Threat Hunting results
- Sysmon Event ID 1
- Parent/child process relationship
- Rule 92066
- MITRE T1059.001 mapping