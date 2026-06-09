# Investigation Report

## Executive Summary

A Sysmon Event ID 1 alert was generated after PowerShell attempted to retrieve content from an external website using Invoke-WebRequest.

The event was analyzed to determine whether the activity represented legitimate administration or potentially malicious download behavior.

The activity was confirmed as a controlled lab simulation.

---

## Alert Information

Event Source: Sysmon

Event ID: 1

Detection Type: Process Creation

Severity: Medium

---

## Investigation Steps

### Step 1

Reviewed Sysmon Event ID 1 logs.

### Step 2

Identified process image:

C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe

### Step 3

Reviewed CommandLine field.

Observed:

Invoke-WebRequest -Uri https://example.com

### Step 4

Reviewed parent process information.

Parent Process:

powershell.exe

### Step 5

Validated activity against lab testing notes.

---

## Findings

PowerShell attempted to connect to:

https://example.com

The request generated an error due to Internet Explorer configuration requirements.

Despite the failure, Sysmon successfully logged the command execution.

This behavior is important because attackers frequently use Invoke-WebRequest to:

- Download malware
- Retrieve payloads
- Stage tools
- Download scripts

---

## MITRE ATT&CK

T1059.001 – PowerShell

T1105 – Ingress Tool Transfer

---

## Conclusion

The activity represented a simulated PowerShell web request.

No malicious activity was identified.

Detection visibility was successfully validated through Sysmon Event ID 1 logging.
