# SOC Investigation Report — Phishing Case-001

## 1. Incident Overview

- **Case ID:** Phishing Case-001
- **Original Training Incident ID:** 003
- **Investigation:** Payroll Phishing and Encoded Attachment
- **Email Date:** March 31, 2026
- **Original Report Date:** April 6, 2026
- **Environment:** Simulated Phishing Scenario
- **Classification:** Simulated Phishing Attempt
- **Severity:** Medium

## 2. Executive Summary

Investigated a simulated phishing email impersonating an HR department and requesting that an employee review an attached payroll document.

The message used salary-processing pressure, failed sender authentication, and an attachment containing Base64-encoded text describing a simulated PowerShell download-and-execute command.

The evidence supports a phishing training scenario. No actual command execution, credential theft, or endpoint compromise was established.

## 3. Indicators of Interest

| Indicator | Finding |
|---|---|
| Sender | `hr@company-payroll.com` |
| Subject | Updated Payroll Information - Action Required |
| Sending Server | `mail.company-payroll.com` |
| External IP | `203.0.113.55` — documentation address |
| Internal IP | `192.168.1.10` — private address |
| SPF | Fail |
| DKIM | None |
| DMARC | Fail |
| Attachment Name | `Payroll_Update.doc` |
| MIME Type | `application/octet-stream` |
| Encoding | Base64 |

The IP addresses are consistent with a simulated environment and are not confirmed malicious indicators.

## 4. Investigation Findings

**Email Authentication:** The supplied header reports SPF failure, no DKIM signature, and DMARC failure. These findings support suspicion but do not independently establish malicious intent.

**Sender and Routing:** The message claims to represent HR. Its Received chain contains documentation and private IP addresses, consistent with training data. Neither address establishes an exfiltration destination.

**Social Engineering:** The email requests payroll information review and warns of delayed salary processing. This creates pressure to interact with the attachment.

**Attachment Analysis:** The MIME structure identifies a Base64-encoded attachment named `Payroll_Update.doc`. Its declared MIME type is `application/octet-stream`; the actual file format was not verified.

**Encoded Content:** The supplied Base64 text contains a simulated malicious-file description and PowerShell download-and-execute syntax referencing a demonstration payload URL.

**Execution Review:** No evidence establishes that the attachment was opened, the command executed, or any information was stolen.

## 5. MITRE ATT&CK Mapping

**T1566.001 — Phishing: Spearphishing Attachment**

The simulated email uses an attachment as its intended delivery mechanism.

The encoded text also references PowerShell execution behavior, but execution was not observed.

## 6. Assessment and Escalation

**Classification:** Simulated Phishing Attempt.

**Recommended Actions in a Real SOC Environment:**

- Quarantine the suspicious message pending investigation.
- Verify the claimed HR request through an independent channel.
- Preserve and analyze the attachment in an approved isolated environment.
- Search for similar messages and recipient interaction.
- Escalate if endpoint telemetry confirms attachment execution or compromise.

## 7. Conclusion

The supplied evidence demonstrates a simulated HR payroll phishing attempt using urgency, failed email authentication, and encoded attachment content.

No real attacker infrastructure, successful payload execution, credential harvesting, or system compromise was established.

## 8. Evidence Reference

- `evidence/case3_header.txt`
- `evidence/case3_body.txt`
- `evidence/raw_base64.txt`
- `evidence/clean_base64.txt`
- `evidence/attachment_base64.txt`

**Source:** Independent simulated phishing investigation.
