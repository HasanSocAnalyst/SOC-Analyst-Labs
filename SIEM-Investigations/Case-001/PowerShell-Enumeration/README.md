# SIEM-001 – Suspicious PowerShell Enumeration Activity

---

## Case Objective

Brief description of what this investigation demonstrates.

---

## Lab Environment

Operating System:
Windows 10 22H2

PowerShell:
5.1

Splunk Enterprise:
9.4.6

Splunk Universal Forwarder:
10.4.1

Sysmon:
15.20

PowerShell Script Block Logging:
Enabled

Sysmon Operational Logging:
Enabled

---

## MITRE ATT&CK

Technique:
T1059.001 – PowerShell

Technique:
T1033 – System Owner/User Discovery

Technique:
T1082 – System Information Discovery

Technique:
T1007 – Service Discovery

Technique:
T1046 – Network Service Discovery

---

## Windows Commands Used

whoami

hostname

Get-Date

Get-Process

Get-Service

Get-NetAdapter

Get-NetIPAddress

Get-ComputerInfo

Get-PSDrive

---

## Expected Telemetry

Sysmon Event ID 1

PowerShell Event ID 4104

PowerShell Operational Logs

Splunk Universal Forwarder

---

## Expected Learning Outcomes

Learn how to investigate PowerShell execution.

Identify Event ID 4104.

Correlate Sysmon with PowerShell logs.

Map activity to MITRE ATT&CK.

Document findings using a professional SOC analyst workflow.
