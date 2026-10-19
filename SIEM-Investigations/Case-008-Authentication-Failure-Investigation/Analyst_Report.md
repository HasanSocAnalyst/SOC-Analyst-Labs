# Analyst Report — SIEM-008

**Case:** Authentication Failure Investigation  
**Date:** October 18, 2026  
**Affected Host:** DESKTOP-H6J6VE5  
**Account:** SOC_Lab  
**Source IP:** 192.168.56.102  
**Environment:** Authorized SOC Lab  
**Classification:** Simulated Suspicious Authentication  
**Severity:** Low (lab context)

## 1. Alert Summary

A Splunk detection identified seven failed authentication events within a five-minute interval against the SOC_Lab account.

The activity was investigated to determine whether repeated credential failures were followed by successful authentication and potentially malicious process execution.

## 2. Investigation Findings

**Authentication Analysis**

- Windows Security Event ID 4625 confirmed seven failed logons.
- Failure details included incorrect credentials.
- Relevant failed logons used Logon Type 7.
- Windows Security Event ID 4624 confirmed successful authentication events, including later Type 7 events.
- The authentication sequence raised a password-guessing hypothesis, but the available evidence did not confirm unauthorized access.

**Endpoint Investigation**

- Sysmon Event ID 1 was reviewed for process activity after the successful authentication events.
- Most reviewed processes were consistent with Windows or installed application activity.
- DismHost.exe executed from a temporary directory, prompting additional investigation.
- Its parent process was cleanmgr.exe with an `/autoclean /d C:` command line, consistent with Windows Disk Cleanup.
- No confirmed malicious process execution was identified.

## 3. MITRE ATT&CK

**T1110 — Brute Force**

The repeated authentication failures resemble behavior that may be associated with password guessing. This mapping represents the detection hypothesis, not confirmation that a brute-force attack occurred.

## 4. Risk and Response

In a production environment, repeated failed authentication attempts followed by successful authentication should prompt validation of account activity, source-system ownership, and user authorization.

Recommended actions:

- Verify whether the account owner initiated the authentication attempts.
- Review the originating system and relevant authentication records.
- Correlate successful sessions with endpoint activity.
- Escalate unexplained or unauthorized activity according to organizational procedures.

## 5. Final Assessment

**Disposition: Authorized simulation — no confirmed compromise.**

The investigation successfully detected a repeated authentication-failure pattern and correlated it with subsequent successful authentication events.

The available telemetry did not establish successful malicious password guessing, unauthorized access, or malicious post-authentication activity.

The case demonstrates practical SOC Tier 1 detection, triage, event correlation, and defensible incident reporting.
