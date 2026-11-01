# SOC Investigation Report — PH-010

## 1. Incident Overview

- **Portfolio Case:** Phishing Case-002
- **Training Sequence:** PH-010
- **Investigation:** Cloud Storage Payment Phishing
- **Email Date:** October 18, 2026
- **Evidence Source:** Original Gmail Spam Email (.eml)
- **Tools:** Python, Email Headers, MIME Analysis
- **Classification:** Phishing — High Confidence
- **Severity:** Medium

## 2. Executive Summary

Investigated an email claiming that cloud-storage payment renewal had failed and threatening deletion of stored photos and videos.

Static analysis identified inconsistent sender identities, suspicious payment-update links, misleading trust messaging, and urgency-based social engineering.

SPF and DKIM passed for domains associated with the sender infrastructure but did not authenticate the claimed cloud-storage provider.

The evidence supports phishing. No successful credential theft, payment-data theft, or endpoint compromise was confirmed.

## 3. Indicators of Interest

| Indicator | Finding |
|---|---|
| Visible From Domain | `vmmml.mdz` |
| Return-Path Domain | `one.ass0035.banozeka.my.id` |
| DKIM Signing Domain | `500.822140.eZ5i.one.ass0035.banozeka.my.id` |
| Sending IP | `118.107.216.227` |
| Suspicious Third-Party Hostname | `pyzmxyj.com` |
| Payment-Link Hostname | `storage.googleapis.com` |
| Payment-Link Path | `/strow/strw-v1-cl1.html` |
| SPF | Pass |
| DKIM | Pass |
| DMARC | Not reported in visible authentication results |

## 4. Investigation Findings

**Sender Analysis:** The visible sender, Sender header, and Return-Path used inconsistent identities. The displayed sender name resembled the recipient rather than an identifiable cloud-storage provider.

**Authentication:** SPF and DKIM passed, but the authenticated domains did not establish legitimacy of the claimed cloud-storage service.

**URL Analysis:** Five URLs were extracted across two hostnames. The payment-update button directed recipients to a cloud-hosted HTML page rather than a verified billing portal. The destination page was not visited or dynamically analyzed.

**Social Engineering:** The subject threatened deletion on October 18, 2026, the same date as the message. The email body requested urgent payment updates and included a misleading trusted-sender statement.

**MIME Analysis:** The message used `multipart/digest` with three HTML parts. Python identified two parts as attachments, but no attachment filenames or explicit attachment dispositions were present. No malicious attachment was established.

## 5. MITRE ATT&CK Mapping

**T1566.002 — Phishing: Spearphishing Link**

The email used a deceptive payment-update link to encourage recipient interaction. The suspected objective was payment-information collection; successful credential or payment-data theft was not observed.

## 6. Assessment and Escalation

**Classification:** Phishing — High Confidence  
**Severity:** Medium  
**Disposition:** Report as phishing; no confirmed compromise.

**Recommended Actions:**
- Report and quarantine the suspicious email.
- Review whether other recipients received similar messages.
- Investigate the extracted URLs using approved threat-intelligence procedures.
- Block confirmed malicious indicators according to organizational policy.
- Escalate for account and payment-security review if recipient interaction is identified.

## 7. Conclusion

The email displayed multiple phishing indicators, including sender inconsistencies, misleading cloud-service branding, suspicious payment-update links, and urgency tactics.

The evidence supports a high-confidence phishing classification. No confirmed compromise or malicious attachment was established.

## 8. Evidence Reference

- `evidence/01-email-header-analysis.png`
- `evidence/02-suspicious-url-analysis.png`
- `evidence/03-phishing-content.png`

**Source:** Real suspicious email obtained from Gmail Spam and analyzed without opening embedded links.
