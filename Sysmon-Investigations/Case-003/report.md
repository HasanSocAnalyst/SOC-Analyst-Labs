# Investigation Report

## Executive Summary

A Sysmon Event ID 1 alert was generated after PowerShell was launched using the ExecutionPolicy Bypass parameter.

The event was reviewed to determine whether the activity represented malicious execution or an authorized administrative action.

Analysis confirmed the activity originated from a controlled lab simulation.

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

powershell.exe -ExecutionPolicy Bypass -NoProfile

### Step 4

Verified parent process information.

Parent Process:

powershell.exe

### Step 5

Confirmed activity was initiated by the lab user.

---

## Evidence

PowerShell process creation event.

ExecutionPolicy Bypass parameter detected.

No malicious payload execution observed.

---

## MITRE ATT&CK

T1059.001 – PowerShell

---

## Conclusion

The event represented a successful PowerShell Execution Policy Bypass simulation.

No indicators of compromise were identified.

Activity was determined to be authorized lab-generated testing.
