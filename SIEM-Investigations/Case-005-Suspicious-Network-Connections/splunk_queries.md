# Splunk Investigation Queries

Case ID: 005

Case Name: Suspicious PowerShell Network Connection

Analyst: Hasan B.

Date:

---

# Query 1

## Objective

Find all Sysmon network connections

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3
```

---

# Query 2

## Objective

Find PowerShell network connections

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3 
Image="*powershell.exe"
| table _time User Image DestinationHostname DestinationIp DestinationPort Protocol Initiated
```                                                         

---

# Query 3

## Objective

Find outbound HTTPS traffic

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3 
DestinationPort=443
| table _time Image DestinationHostname DestinationIp DestinationPort
```
   
---

# Query 4 

## Objective

Find the PowerShell process that generated the connection                                 

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=1 
CommandLine="*Invoke-WebRequest*"
| table _time User ParentImage Image CommandLine                        
```
   
---
