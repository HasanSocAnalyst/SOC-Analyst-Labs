# Sysmon Investigation Case 003

## Title
PowerShell Execution Policy Bypass Detection

## Objective
Investigate Sysmon Event ID 1 generated when PowerShell is launched using the ExecutionPolicy Bypass argument.

## Skills Demonstrated

- Sysmon Event Analysis
- Windows Process Monitoring
- PowerShell Investigation
- Command-Line Analysis
- Threat Hunting

## Detection Source

Sysmon Event ID 1
(Process Creation)

## Command Executed

powershell -ExecutionPolicy Bypass -NoProfile

## Key Findings

The PowerShell process was successfully launched using the ExecutionPolicy Bypass parameter.

This behavior is commonly associated with malware execution, offensive security tooling, and attempts to evade PowerShell security restrictions.

## MITRE ATT&CK

T1059.001 – PowerShell

## Evidence

- Command execution screenshot
- Sysmon Event ID 1 screenshot
- Investigation report

## Conclusion

The activity was confirmed as a benign lab simulation designed to generate telemetry associated with PowerShell execution policy bypass behavior.
