# SIEM-002 — Suspicious Encoded PowerShell Execution

## Objective

Investigate PowerShell activity involving the `-EncodedCommand` parameter and determine whether the execution was 
benign or malicious.

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

* **T1059.001** — PowerShell
* **T1027** — Obfuscated/Compressed Files or Information
* **T1082** — System Information Discovery

---

## Windows Commands Used

### Step 1 — Create encoded command

```powershell
$cmd = 'Get-ComputerInfo'
$bytes = [System.Text.Encoding]::Unicode.GetBytes($cmd)
$encoded = [Convert]::ToBase64String($bytes)
$encoded
```

### Step 2 — Execute encoded PowerShell

```powershell
powershell.exe -EncodedCommand RwBlAHQALQBDAG8AbQBwAHUAdABlAHIASQBuAGYAbwA=
```

---

## Expected Telemetry

* PowerShell Event ID **4104**
* Sysmon Event ID **1**
* Command line containing **-EncodedCommand**
* Decoded script block text showing **Get-ComputerInfo**

---

## Expected Learning Outcomes

* Detect encoded PowerShell execution.
* Identify the `-EncodedCommand` parameter in Sysmon.
* Correlate Sysmon and Event ID 4104 telemetry.
* Decode Base64 PowerShell commands.
* Determine whether the activity is benign or suspicious.

