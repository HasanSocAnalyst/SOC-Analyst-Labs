# SIEM-008 — Authentication Failure Investigation

**Investigation Type:** Windows Authentication / SIEM Analysis  
**Tools:** Splunk Enterprise, Windows Security Logs, Sysmon  
**Environment:** Authorized Windows SOC Lab  
**Classification:** Simulated Suspicious Authentication — No Confirmed Compromise  
**MITRE ATT&CK:** T1110 — Brute Force (behavioral detection hypothesis, not confirmed attack)

## Investigation Summary

Investigated repeated failed Windows authentication events against the `SOC_Lab` account on `DESKTOP-H6J6VE5`.

Splunk identified seven failed logons within a five-minute interval from `192.168.56.102`. Subsequent successful authentication events were also observed. The relevant failed and later successful events used Logon Type 7 (workstation unlock).

## Key Findings

- **Event ID 4625:** Seven failed authentication events detected.
- **Event ID 4624:** Successful authentication events observed, including events following the failure sequence.
- **Source IP:** `192.168.56.102`
- **Account:** `SOC_Lab`
- **Failure reason:** Incorrect credentials.
- **Sysmon Event ID 1:** Reviewed post-authentication process activity.
- **Process validation:** `DismHost.exe` was launched by `cleanmgr.exe`, consistent with Windows maintenance.
- **Impact:** No confirmed unauthorized access or malicious post-authentication execution.

## Evidence

1. [Failed logon detection](evidence/01-failed-logon-detection.png)
2. [Failed logon details](evidence/02-failed-logon-details.png)
3. [Authentication correlation](evidence/03-successful-authentication.png)
4. [Post-login process review](evidence/04-post-login-process-review.png)
5. [DismHost process validation](evidence/05-dismhost-parent-process.png)

## SOC Decision

The authentication pattern warrants investigation in a production environment, but the evidence does not establish successful password guessing or account compromise.

**Disposition:** Authorized lab simulation; suspicious authentication pattern reproduced. No confirmed compromise.

## Skills Demonstrated

Splunk SPL, Windows Event ID 4624/4625 analysis, authentication correlation, detection thresholds, Sysmon process investigation, and evidence-based SOC reporting.
