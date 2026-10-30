# SIEM-005 — Suspicious PowerShell Network

## Objective

Investigate an outbound HTTPS connection initiated by PowerShell using Sysmon and Splunk to 
determine the originating process, destination, and whether the activity represents benign or 
suspicious behavior.

## Environment

* Windows version - 10 22H2
* Splunk version - 9.4.6
* Sysmon version - 15.20
* PowerShell version - 5.1

## Telemetry Generated

Generate Outbound HTTPS traffic: powershell.exe -Command "Invoke-WebRequest 
https://www.microsoft.com"

Verify Active Network Connections: netstat -ano


## Splunk Investigation

### Search 1 — Find all Sysmon network connections

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3
```

### Search 2 — Find PowerShell network connections

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3 
Image="*powershell.exe"
| table _time User Image DestinationHostname DestinationIp DestinationPort Protocol Initiated
```

### Search 3 —  Find outbound HTTPS traffic

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3 
DestinationPort=443
| table _time Image DestinationHostname DestinationIp DestinationPort
```

### Search 4 — Find the PowerShell process that generated the connection

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=1 
CommandLine="*Invoke-WebRequest*"
| table _time User ParentImage Image CommandLine
```

## MITRE ATT&CK

* T1059.001 — PowerShell
* T1071.001 — Application Layer Protocol: Web Protocols
* T1105 - Ingress Tool Transfer

## Result

* What was confirmed
- HTTPS connection was initiated by PowerShell
- Logged-on user executed PowerShell using the Invoke-WebRequest
- outbound TCP connection was established over port 443 to www.microsoft.com


* Final classification
- Benign ( Authorized Admin Activity)


## Skills Demonstrated

SIEM Investigation
Splunk Search Processing Language (SPL)
Sysmon Log Analysis
PowerShell Forensics
Process Correlation
Network Connection Analysis
MITRE ATT&CK Mapping
Threat Detection
Incident Investigation Workflow


