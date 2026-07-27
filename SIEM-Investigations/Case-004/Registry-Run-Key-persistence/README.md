# SIEM-004 — Registry Run Key Persistence

## Objective

Investigate the creation of a Windows Registry Run key used for persistence, identify the 
registry modification in Splunk, correlate the activity with PowerShell execution, and 
determine whether the persistence mechanism is benign or suspicious.

---

## Lab Environment

* Windows 10 22H2
* PowerShell 5.1
* Sysmon 15.20
* Splunk Enterprise 9.4.6
* Universal Forwarder 10.4.1
* Sysmon Logging: Enabled
* Registry Monitoring: Enabled

---

## MITRE ATT&CK

* **T1547.001** — Registry Run Keys / Startup Folder
* **T1059.001** — PowerShell

---

## Windows Commands Used

### Step 1 — Create the Registry Run key

```powershell
New-ItemProperty `
-Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" `
-Name "WindowsUpdate" `
-Value "C:\Windows\System32\notepad.exe" `
-PropertyType String `
-Force
```
### Step 2 — Verify the Registry value

```powershell
Get-ItemProperty "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run"
```

### Step 3 — Remove the Registry Run key

```powershell
Remove-ItemProperty `
-Path "HKCU:\Software\Microsoft\Windows\CurrentVersion\Run" `
-Name "WindowsUpdate"
```

---

## Expected Telemetry

* Sysmon Event ID **13** (Registry Value Set)
* Sysmon Event ID **1** (PowerShell Process Creation)
* Registry path containing **CurrentVersion\Run**
* Registry value **WindowsUpdate**
* Registry data **C:\Windows\System32\notepad.exe**

---

## Splunk Searches


### Search 1 — Find Registry Run key modifications

```spl
index=main EventCode=13 TargetObject="*CurrentVersion\\Run*"
```

### Search 2 — Find the Registry value

```spl
index=main EventCode=13 Details="*notepad.exe*"
```

---

## Expected Findings

* A Registry Run key named **WindowsUpdate** was successfully created.
* The Run key was configured to launch **Notepad.exe** during user logon.
* Sysmon Event ID **13** recorded the Registry modification.
* PowerShell was identified as the process responsible for creating the persistence mechanism.
* The Registry value was successfully removed after validation.
* Activity was confirmed as authorized lab testing.

---

## Learning Outcomes

* Detect Registry Run key persistence using Sysmon Event ID 13.
* Investigate Windows Registry modifications related to persistence.
* Correlate Registry events with PowerShell process creation.
* Identify common persistence techniques used by attackers.
* Map Registry persistence activity to **MITRE ATT&CK T1547.001**.
* Differentiate between authorized administrative activity and malicious persistence 
mechanisms.
