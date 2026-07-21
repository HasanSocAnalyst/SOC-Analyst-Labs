# SIEM-001 — PowerShell Enumeration Investigation

**Objective:** Investigate suspicious PowerShell activity using Splunk, Sysmon, 
and Windows PowerShell Logging.

## Environment

* Windows 10 22H2
* Splunk Enterprise 9.4.6
* Sysmon 15.20
* PowerShell 5.1

## Telemetry Generated

Executed safe reconnaissance commands:

* `Get-Process`
* `Get-Service`
* `Get-NetAdapter`
* `Get-NetIPAddress`
* `Get-ComputerInfo`
* `Get-PSDrive`

## Splunk Investigation

### PowerShell Script Block Logging

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" EventID=4104
```

Captured the executed commands and confirmed PowerShell enumeration activity.

### Sysmon Process Creation

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 
Image="*powershell.exe"
```

Correlated the PowerShell execution with process creation telemetry and identified the 
execution context.

## MITRE ATT&CK

* **T1059.001** — PowerShell
* **T1057** — Process Discovery
* **T1007** — Service Discovery
* **T1016** — Network Configuration Discovery
* **T1082** — System Information Discovery

## Result

* Confirmed Event ID **4104** PowerShell telemetry.
* Correlated with Sysmon Event ID **1**.
* Built a timeline of reconnaissance activity.
* Determined the activity was **Benign — Authorized Lab Activity**.
* No persistence, malware, or lateral movement observed.

## Skills Demonstrated

Splunk / Sysmon / PowerShell Logging / MITRE ATT&CK / Process Analysis / Timeline Analysis / 
SOC Investigation


