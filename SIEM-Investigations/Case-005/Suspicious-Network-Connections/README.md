# SIEM-005 — Suspicious PowerShell Network Connection

## Objective

Investigate an outbound HTTPS connection initiated by PowerShell using Sysmon and Splunk to 
determine the originating process, destination, and whether the activity represents benign or 
suspicious behavior.

---

## Lab Environment

* Windows 10 22H2
* PowerShell 5.1
* Sysmon 15.20
* Splunk Enterprise 9.4.6
* Universal Forwarder 10.4.1
* Sysmon Network Connection Logging: Enabled

---

## MITRE ATT&CK

* **T1059.001** — PowerShell
* **T1071.001** — Application Layer Protocol: Web Protocols
* **T1105** — Ingress Tool Transfer

---

## Windows Commands Used

### Step 1 — Launch PowerShell and generate outbound HTTPS traffic

```powershell
powershell.exe -Command "Invoke-WebRequest https://www.microsoft.com"
```

---

### Step 2 — Verify active network connections

```powershell
netstat -ano
```

---

## Expected Telemetry

* Sysmon Event ID **1** (Process Creation)
* Sysmon Event ID **3** (Network Connection)
* Image = **powershell.exe**
* CommandLine contains **Invoke-WebRequest**
* Destination Port **443**
* Destination IP Address
* Destination Hostname
* User Account

---

## Splunk Searches

### Search 1 — Find all Sysmon network connections

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3
```

---

### Search 2 — Find PowerShell network connections

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3 
Image="*powershell.exe"
| table _time User Image DestinationHostname DestinationIp DestinationPort Protocol Initiated
```

---

### Search 3 — Find outbound HTTPS traffic

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=3 
DestinationPort=443
| table _time Image DestinationHostname DestinationIp DestinationPort
```

---

### Search 4 — Find the PowerShell process that generated the connection

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventCode=1 
CommandLine="*Invoke-WebRequest*"
| table _time User ParentImage Image CommandLine
```
---

## Expected Findings

* PowerShell was executed by the logged-on user.
* The PowerShell command contained **Invoke-WebRequest**.
* Sysmon recorded an outbound HTTPS connection (Event ID 3).
* The destination hostname and IP address were successfully identified.
* Process creation (Event ID 1) was correlated with the network connection.
* The activity was determined to be authorized lab testing.

---

## Learning Outcomes

* Detect PowerShell-generated outbound network connections.
* Correlate Sysmon Event ID 1 with Event ID 3.
* Identify destination IP addresses, hostnames, and ports.
* Analyze PowerShell network activity within Splunk.
* Map network activity to MITRE ATT&CK techniques.
* Differentiate legitimate administrative activity from suspicious outbound communications 
commonly observed during malware execution and command-and-control activity.
