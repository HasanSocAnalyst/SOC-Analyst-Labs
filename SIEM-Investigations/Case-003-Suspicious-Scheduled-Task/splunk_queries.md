# Splunk Investigation Queries

Case ID: 003

Case Name: Suspicious Scheduled Task

Analyst: Hasan B. 

Date:

---

# Query 1 - Find scheduled task creation 

### Search

```spl
index=main EventCode=4698
```

### Purpose

Verify the task was created 

---

# Query 2 - Show the taks details

### Search  

```spl
index=main EventCode=4698
| table _time host TaskName TaskContent SubjectUserName
```

### Purpose

extract the task name, XML content, and user who created the task     
   
---

# Query 3 - Look for PowerShell       

### Search

```spl
index=main EventCode=4698 "powershell.exe"
```

### Purpose

Identify scheduled tasks that execute PowerShell
   
---

# Query 4 - Correlate with Sysmon process creation  
   
### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 
Image="*schtasks.exe"
| table _time User ParentImage Image CommandLine          
```                                                    
   
### Purpose

view the schedule tasks command that was executed & which user                 

---
