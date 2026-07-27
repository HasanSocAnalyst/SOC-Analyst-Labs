# SIEM-003 — Suspicious Scheduled Task Persistence

## Objective

Investigate the creation of a Windows scheduled task that could be used for persistence and 
determine whether the activity is benign or suspicious.

---

## Lab Environment

* Windows 10 22H2
* PowerShell 5.1
* Sysmon 15.20
* Splunk Enterprise 9.4.6
* Universal Forwarder 10.4.1
* PowerShell Script Block Logging: Enabled
* Sysmon Logging: Enabled

---

## MITRE ATT&CK

* **T1053.005** — Scheduled Task / Job: Scheduled Task
* **T1059.001** — PowerShell
* **T1547** — Boot or Logon Autostart Execution

---

## Windows Commands Used

### Step 1 — Create the scheduled task

```powershell
schtasks /create /tn "UpdaterTask" /tr "powershell.exe -Command Get-Date" /sc onlogon /ru 
$env:USERNAME
```

### Step 2 — Verify the task

```powershell
schtasks /query /tn "UpdaterTask" /fo LIST /v
```

---

## Expected Telemetry

* Security Event ID **4698** (scheduled task creation)
* Sysmon Event ID **1** (process creation)
* Command line containing **schtasks /create**
* Task action containing **powershell.exe -Command Get-Date**
* Trigger type **ONLOGON**

---

## Splunk Searches

### Search 1 — Find scheduled task creation

```spl
index=main EventCode=4698
```

### Search 2 — Display task details

```spl
index=main EventCode=4698
| table _time host TaskName TaskContent SubjectUserName
```

### Search 3 — Find PowerShell within task actions

```spl
index=main EventCode=4698 "powershell.exe"
```

### Search 4 — Correlate with Sysmon process creation

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 
Image="*schtasks.exe"
| table _time User ParentImage Image CommandLine
```

---

## Expected Findings

* A scheduled task named **UpdaterTask** was created.
* The task is configured to run **at user logon**.
* The task action launches **PowerShell**.
* Sysmon captured the execution of **schtasks.exe** with the full command line.

---

## Learning Outcomes

* Detect scheduled task creation using Security Event ID 4698.
* Identify PowerShell-based persistence mechanisms.
* Correlate Security logs with Sysmon process creation events.
* Analyze scheduled task actions and triggers.
* Map persistence activity to **MITRE ATT&CK T1053.005**.
* Determine whether a scheduled task represents benign administrative activity or suspicious 
persistence.

