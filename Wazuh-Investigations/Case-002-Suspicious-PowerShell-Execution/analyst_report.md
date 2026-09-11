# WAZUH-002 — Suspicious PowerShell Execution

## Objective

Investigate a PowerShell execution detected by Wazuh and determine whether the activity is benign or suspicious.

---

## Environment

* Windows - Windows 10 22H2
* Wazuh - 4.14.7
* Agent - 4.14.7
* Tools - Wazuh Dashboard, PowerShell

---

## Telemetry Generated

```text
Get-ComputerInfo

Get-Service

Get-Process
```

---

# Investigation

## Alert

**Source**

PowerShell

**Rule ID**

(Record Rule ID)

**Severity**

(Record Alert Level)

**Endpoint**

SOC-WIN10

---

## Findings

* PowerShell execution was detected by Wazuh.
* Telemetry was successfully collected from the endpoint.
* The activity originated from SOC-WIN10.
* The alert mapped to MITRE ATT&CK T1059.001.

---

# MITRE ATT&CK

* T1059.001 — Command and Scripting Interpreter: PowerShell

---

# Analyst Assessment

**Root Cause**

Administrative PowerShell commands executed by the analyst.

**Impact**

No malicious activity observed.

**Evidence**

PowerShell process, Wazuh alert, endpoint information, and MITRE mapping.

**Confidence**

High

---

# Result

**Classification**

Benign

**Recommendation**

Continue monitoring PowerShell activity for suspicious or encoded commands.

---

# Skills Demonstrated

* Wazuh Investigation
* Alert Analysis
* Endpoint Analysis
* Rule Analysis
* MITRE ATT&CK Mapping
* Incident Investigation Workflow
