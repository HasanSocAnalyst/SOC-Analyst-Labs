# Case-001 — Payroll Phishing and Encoded Attachment Analysis

**Investigation Type:** Phishing Email / Attachment Analysis  
**Evidence Source:** Simulated Email and Base64 Artifacts  
**Tools:** Linux Terminal, Email Headers, Base64 Analysis  
**Classification:** Simulated Phishing Attempt  
**Severity:** Medium  
**MITRE ATT&CK:** T1566.001 — Phishing: Spearphishing Attachment

## Investigation Summary

Investigated a simulated payroll-themed phishing email impersonating an HR department.

Reviewed sender authentication, email routing, social engineering indicators, and a Base64-encoded attachment containing a simulated PowerShell download-and-execute command.

## Key Findings

- **Subject:** Updated Payroll Information - Action Required
- **Sender:** `hr@company-payroll.com`
- **Authentication:** SPF failed, DKIM absent, DMARC failed.
- **Social Engineering:** Threat of delayed salary processing.
- **Attachment:** `Payroll_Update.doc`, labeled `application/octet-stream`.
- **Encoded Content:** Base64 text describing a simulated PowerShell download-and-execute command.
- **Execution:** No command execution or compromise confirmed.
- **Environment:** Simulated training scenario.

## Evidence

- [Email Header](evidence/case3_header.txt)
- [Email Body and Attachment](evidence/case3_body.txt)
- [Original Base64 Artifact](evidence/raw_base64.txt)
- [Cleaned Base64 Artifact](evidence/clean_base64.txt)
- [Attachment Base64 Artifact](evidence/attachment_base64.txt)

## Disposition

**Simulated Phishing Attempt.**

The message demonstrates HR impersonation, urgency-based social engineering, failed sender authentication, and suspicious encoded attachment content.

No real-world compromise or payload execution was established.

## Skills Demonstrated

Email Header Analysis · SPF/DKIM/DMARC Interpretation · Base64 Analysis · Attachment Triage · MITRE ATT&CK Mapping · Evidence-Based Classification

[Read the full investigation report](analyst_report.md)
