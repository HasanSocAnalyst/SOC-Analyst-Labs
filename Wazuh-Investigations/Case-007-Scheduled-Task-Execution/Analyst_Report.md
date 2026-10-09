# Analyst Report — Scheduled Task Execution

**Case ID:** Case-007  
**Date:** 2026-10-07  
**Host:** SOC-WIN10 (DESKTOP-H6J6VE5)  
**User:** SOC_Lab  
**Tools:** Wazuh, Splunk, Sysmon

## Alert Summary
Suspicious Windows scheduled-task activity was investigated following the execution of `WindowsCacheMaintenance`, which referenced a batch file located in the user's temporary directory.

## Key Evidence
1. **Task Creation:** `schtasks.exe /Create` configured `WindowsCacheMaintenance` with an `ONLOGON` trigger and an action referencing `maint.cmd`.
2. **Task Execution:** `schtasks.exe /Run` initiated the registered task.
3. **Process Ancestry:** Task Scheduler's `svchost.exe` spawned `cmd.exe` (PID 6804), executing `maint.cmd`.
4. **Child Processes:** Sysmon recorded `whoami.exe` (PID 6184) and `hostname.exe` (PID 6156), both launched by PID 6804.
5. **Additional Activity:** PowerShell telemetry showed execution of `update.ps1`, but its direct relationship with the scheduled-task process chain remained unconfirmed.

## Analysis
The scheduled task executed a batch file from a temporary directory, a behavior that warrants investigation because scheduled tasks can be abused for persistence.

The process chain confirmed subsequent system and user discovery commands. Matching logon identifiers supported session correlation but did not independently establish a relationship with the separate PowerShell activity.

## MITRE ATT&CK
- **T1053.005:** Scheduled Task
- **T1059.003:** Windows Command Shell
- **T1033:** System Owner/User Discovery
- **T1082:** System Information Discovery

## Final Assessment
**Benign True Positive — Controlled Simulation**

The detected activity was generated intentionally for SOC training. Scheduled-task execution and child-process activity were confirmed. No unauthorized compromise was established.

**Disposition:** Closed — Authorized Lab Activity.
