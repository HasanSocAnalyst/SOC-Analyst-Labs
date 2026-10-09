# Case-007 — Scheduled Task Execution Investigation

**Date:** October 7, 2026  
**Environment:** Windows 10 | Sysmon | Wazuh | Splunk  
**Classification:** Benign True Positive — Authorized Lab Simulation  
**MITRE ATT&CK:** T1053.005 — Scheduled Task/Job: Scheduled Task

## Overview
Investigated suspicious scheduled-task activity involving `schtasks.exe` and a batch file executed from a temporary Windows directory.

## Investigation Findings
- Identified the scheduled task `WindowsCacheMaintenance`, configured with an `ONLOGON` trigger.
- Confirmed task execution using `schtasks.exe /Run`.
- Correlated Sysmon Event ID 1 telemetry in Wazuh and Splunk.
- Identified Task Scheduler launching `cmd.exe` (PID 6804) to execute `maint.cmd`.
- Confirmed child processes `whoami.exe` and `hostname.exe`, indicating host and user discovery activity.
- Identified separate PowerShell activity involving `update.ps1`; a direct execution relationship was not established.

## Evidence
- Windows scheduled-task creation and execution
- Wazuh process creation and alert telemetry
- Splunk task execution and process ancestry correlation
- PowerShell script-block and process execution telemetry

## Conclusion
The investigation confirmed scheduled-task execution and subsequent discovery commands. The activity was intentionally generated in an authorized lab environment. No real-world compromise was established.

**Skills Demonstrated:** Alert triage, Sysmon analysis, SPL searches, process correlation, MITRE ATT&CK mapping, and evidence-based reporting.
