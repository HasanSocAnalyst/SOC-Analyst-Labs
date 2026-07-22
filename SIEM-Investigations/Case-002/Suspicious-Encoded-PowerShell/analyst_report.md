# SIEM-002 — Suspicious Encoded PowerShell Execution

## Objective

Investigated PowerShell execution using the -EncodedCommand parameter with Splunk, Sysmon, and PowerShell 
Script Block Logging.

## Environment

* Windows version - Windows 10 22H2
* Splunk version - Splunk Enterprise 9.4.6
* Sysmon version - 15.20
* PowerShell version - 5.1

## Telemetry Generated

$cmd = 'Get-ComputerInfo'
$bytes = [System.Text.Encoding]::Unicode.GetBytes($cmd)
$encoded = [Convert]::ToBase64String($bytes)
$encoded

Base64 String result: RwBlAHQALQBDAG8AbQBwAHUAdABlAHIASQBuAGYAbwA=

powershell.exe -EncodedCommand RwBlAHQALQBDAG8AbQBwAHUAdABlAHIASQBuAGYAbwA=

Decoded: Get-ComputerInfo

## Splunk Investigation

### Search 1 — Verify PowerShell telemetry

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational"
```

### Search 2 — Identify PowerShell Script Block events

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" EventID=4104
| table _time ScriptBlockText
```

### Search 3 — Detect Encoded PowerShell execution

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 "-EncodedCommand"
| table _time User ParentImage Image CommandLine
```

## MITRE ATT&CK

* T1059.001 — PowerShell
* T1027 — Obfuscated / Compressed Files or Information
* T1082 - System Information Discovery

## Result

Encoded - RwBlAHQALQBDAG8AbQBwAHUAdABlAHIASQBuAGYAbwA=

Decoded - Get-ComputerInfo
- Get-ComputerInfo performs system information discovery by collecting operating system, hardware, patch, 
and configuration details

* What was confirmed
- the user launched PowerShell with a Base64-encoded command: powershell.exe -EncodedCommand 
RwBlAHQALQBDAG8AbQBwAHUAdABlAHIASQBuAGYAbwA=  

* What was ruled out
- no data/information was exfiltrated
- No malicious child processes were observed
 
* Final classification
- Benign — Authorized Lab Activity

## Skills Demonstrated

Splunk Search & Reporting

Sysmon Event Analysis

PowerShell Script Block Logging

Event ID 4104 Investigation

Base64 Decoding

Process Creation Analysis

Timeline Analysis

MITRE ATT&CK Mapping

SOC Case Documentation

Event Correlation

