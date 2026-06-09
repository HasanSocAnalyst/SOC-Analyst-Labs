# Sysmon Investigation Case 004

## Title

PowerShell Invoke-WebRequest Detection

## Objective

Investigate Sysmon Event ID 1 generated when PowerShell attempts to retrieve content from a remote web resource.

## Skills Demonstrated

- Sysmon Analysis
- Process Creation Investigation
- Command-Line Analysis
- PowerShell Monitoring
- Threat Hunting

## Detection Source

Sysmon Event ID 1

## Command Executed

Invoke-WebRequest -Uri https://example.com

## Key Findings

PowerShell attempted to execute an Invoke-WebRequest command targeting an external URL.

Although the request did not complete successfully, Sysmon captured the command-line activity.

## MITRE ATT&CK

T1059.001 – PowerShell

T1105 – Ingress Tool Transfer

## Evidence

- PowerShell execution screenshot
- Sysmon Event ID 1 screenshot
- Investigation report

## Conclusion

The activity generated telemetry commonly associated with malware download attempts and was successfully detected through Sysmon logging.
