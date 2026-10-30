# SOC Investigation Report — SIEM-009

## 1. Incident Overview

- **Case ID:** SIEM-009
- **Investigation:** Suspicious Windows Service Creation
- **Date:** October 30, 2026
- **Environment:** Windows 10 SOC Lab
- **Detection Source:** Windows System Event ID 7045
- **Tools:** Splunk, Sysmon
- **Disposition:** Benign True Positive

## 2. Executive Summary

Investigated the installation of `SOC Lab Test Service` on workstation `DESKTOP-H6J6VE5`.

Windows Event ID 7045 confirmed service installation. Sysmon Event ID 1 identified `sc.exe` launched by PowerShell under the `SOC_Lab` account.

The activity was an authorized lab simulation. No service execution was confirmed in the reviewed telemetry.

## 3. Indicators of Interest

| Indicator | Finding |
|---|---|
| Host | `DESKTOP-H6J6VE5` |
| Service | `SOC Lab Test Service` |
| Service Executable | `C:\Windows\System32\cmd.exe /c exit 0` |
| Creating Process | `C:\Windows\System32\sc.exe` |
| Parent Process | `powershell.exe` |
| Executing Account | `DESKTOP-H6J6VE5\SOC_Lab` |
| Service Account | `LocalSystem` |

## 4. Investigation Findings

**Service Installation:** Event ID 7045 confirmed successful creation of a manually started service configured to run as LocalSystem.

**Process Correlation:** Sysmon Event ID 1 recorded `sc.exe` executing the service-creation command, launched by PowerShell.

**Execution Review:** No service execution was confirmed. A manual startup configuration does not independently establish whether a service executed.

**Security Assessment:** The command interpreter and privileged service account warranted investigation, but neither independently established malicious behavior.

## 5. MITRE ATT&CK Mapping

**T1543.003 — Create or Modify System Process: Windows Service**

Technique demonstrated through authorized service creation. Malicious persistence was not established.

## 6. Assessment and Escalation

**Classification:** Benign True Positive.

**Disposition:** Close as authorized lab activity.

**Recommended Actions:**
- Verify authorization of the service installation.
- Preserve relevant Windows and Sysmon evidence.
- Remove the test service after completing the investigation.

## 7. Conclusion

Windows and Sysmon telemetry confirmed service installation through PowerShell and `sc.exe`.

The event represented authorized lab activity. No malicious execution or persistence was established.

## 8. Evidence Reference

- `evidence/01-service-installation.png`
- `evidence/02-sysmon-process-creation.png`
- `evidence/03-service-state.png`

**Source:** Independent Windows SOC lab simulation.
