# SIEM-004 — Registry Run Key Persistnece

## Objective

Simulate an attacker establishing persistence by creating a Windows Run registry key, then 
investigate the activity in Splunk.

## Environment

* Windows version - Windows 10 22H2
* Splunk version - Splunk Enterprise 9.4.6
* Sysmon version - 15.20
* PowerShell version - 5.1

## Telemetry Generated

* Registry Run Key Generatin
New-ItemProperty `
-Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" `
-Name "WindowsUpdate" `
-Value "C:\Windows\System32\notepad.exe" `
-PropertyType String `
-Force

* Clean Up
Remove-ItemProperty `
-Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" `
-Name "WindowsUpdate"

## Splunk Investigation

### Search 1 — Find Registry Run key modifications

```spl
index=main EventCode=13 TargetObject="*CurrentVersion\\Run*"
```

### Search 2 — Find the Registry value

```spl
index=main EventCode=13 Details="*notepad.exe*"
```


## MITRE ATT&CK

* T1059.001 — PowerShell
* T1547.001 — Registry Run Keys / Startup Folder

## Result

* What was confirmed
- A Registry Run key named **WindowsUpdate** was created under the current user's Run registry 
hive.
- The registry value configured **Notepad.exe** to execute during user logon.
- Sysmon Event ID 13 successfully recorded the registry modification.
- PowerShell was identified as the process responsible for creating the persistence mechanism.

* What was ruled out
- No additional persistence methods or malicious payloads were observed.
- Activity was confirmed as authorized laboratory testing.

* Final classification

- Benign - Authorized Lab Activity

## Skills Demonstrated

- Splunk Search Processing Language (SPL)
- Sysmon Event Analysis
- Windows Registry Forensics
- Persistence Detection
- Event Correlation
- MITRE ATT&CK Mapping
- Incident Documentation
- Threat Hunting Fundamentals



