# Splunk Investigation Queries

Case ID: 001

Case Name: Suspicious Powershell Enumeration Activity

Analyst: Hasan B.

Date:

---

# Query 1

## Objective

Verify Sysmon is receiving events.

### Search

```spl
index=main 
source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational"

# Query 2

## Objective

Locate PowerSHell executions

### Search
spl
index=main powershell

# Query 3

## Objective

Review Process Creation Events

### Search
spl
index=main 
source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1

# Query 4

## Objective

Verify the different Event IDs and  how many Event IDs there were generated 

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational"
| stats count by EventID

# Query 5

## Objective

Check which command wewre executed 

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" 
EventID=4104

# Query 6

## Objective

Find Service enumeration                                         

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" 
EventID=4104
Get-Service

# Query 7

## Objective

Locate Operating system discovery          

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" 
EventID=4104
Get-ComputerInfo

# Query 8
   
## Objective

Locate the PowerShell process creation

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" 
EventID=1 Image="*powershell.exe"

# Query 9

## Objective

Build the process execution timeline

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" 
EventID=1 Image="*powershell.exe"
| table _time Computer User ParentImage Image CommandLine ProcessGuid

# Query 10

## Objective
   
Identify which processes are making new processes  

### Search
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" 
EventID=1
| stats count by ParentImage
