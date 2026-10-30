# SIEM-003 — Suspicious Scheduled Task

## Objective

Investigate the creation of a scheduled task that could be used for persistence and determine 
whether the activity is benign or suspicious.

## Environment

* Windows version - Windows 10 22H2
* Splunk version - Splunk Enterprise 9.4.6
* Sysmon version - 15.20
* PowerShell version - 5.1

## Telemetry Generated

schtasks /create /tn "UpdaterTask" /tr "powershell.exe -Command Get-Date" /sc onlogon /ru 
$env:USERNAME

## Splunk Investigation

### Search 1 — Find scheduled task creation

```spl
index=main EventCode=4698
```

### Search 2 — Show the task details

```spl
index=main EventCode=4698
| table _time host TaskName TaskContent SubjectUserName
```

### Search 3 — Look for PowerShell

```spl
index=main EventCode=4698 "powershell.exe"
```

### Search 4 — Correlate with Sysmon process creation

```spl  
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 
Image="*schtasks.exe"
| table _time User ParentImage Image CommandLine
```

## MITRE ATT&CK

* T1053.005 — Scheduled Task
* T1059.001 — PowerShell
* T1547 - Boot or Logon Autostart Execution

## Result

* What was confirmed
- Scheduled task creation occured 
- Task name: UpdaterTask
- Trigger: ONLOGON
- Action: powershell.exe -Command Get-Date
- Sysmon captured the schtask.exe execution

* What was ruled out
- No encoded PowerShell observed 
- No external network connection observed 

* Final classification

- Benign - Authorized Lab Activity

## Skills Demonstrated

Splunk Search & Reporting

Sysmon Event Analysis

PowerShell Script Block Logging

Event ID 4698 Investigation

MITRE ATT&CK Mapping

SOC Case Documentation

Event Correlation


