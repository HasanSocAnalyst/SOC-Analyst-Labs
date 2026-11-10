# Analyst Report — Case-003
## State Farm Garmin Dash Cam Reward Phishing

### 1. Incident Overview

**Case ID:** Case-003  
**Incident Type:** Email Phishing  
**Classification:** Brand-Impersonation Phishing  
**Severity:** High-confidence phishing attempt  
**Status:** Investigation completed  
**Evidence Source:** Unsolicited Gmail email  
**Email Date:** 27 October 2026

### 2. Executive Summary

An unsolicited email impersonating State Farm claimed the recipient had been selected to receive a Garmin Dash Cam reward.

Header analysis identified a mismatch between the claimed brand and the actual sender domain. The reward and unsubscribe links directed recipients to an HTML page hosted on Google Cloud Storage.

Additional examination identified substantial unrelated content appended after the closing HTML document.

The evidence supports a high-confidence phishing classification. No credential submission, malware execution, or compromise was confirmed.

### 3. Indicators of Interest

| Indicator | Observed Value |
|---|---|
| Display Name | State-Farm |
| Sender Domain | `cuzopyhwz.us` |
| Return-Path Domain | `coffeesforacause.com` |
| Sending IP | `217.182.128.98` |
| Sending Host | `fiberseconds.com` |
| Hosting Organization | OVH SAS |
| Hosting Country | France |
| Reward URL Host | `storage.googleapis.com` |
| Image Host | `i.imgur.com` |

### 4. Investigation Findings

**Email Authentication**

- SPF: PASS for the Return-Path domain.
- DKIM: No signature present in the supplied headers.
- DMARC: No result reported.
- The SPF result did not authenticate the claimed State Farm identity.

**Sender Infrastructure**

WHOIS investigation associated `217.182.128.98` with OVH SAS, France, under AS16276.

This identifies the network allocation and hosting organization but does not independently establish malicious activity.

**URL Analysis**

The reward and unsubscribe links both pointed to:

`storage.googleapis.com/usales26/usales26.html`

Their encoded fragments contained different action parameters. The destination was not opened.

**HTML Analysis**

The main HTML document closed at line 202. Unrelated content began at line 204 and continued through line 631.

The additional content included unrelated newsletter fragments, citrus-tree information, random-looking strings, and unrelated membership messages.

This may represent HTML content padding or possible filter-evasion behavior. The intended purpose was not established.

**Impact Assessment**

No evidence of credential submission, malware execution, or account compromise was identified during this investigation.

### 5. MITRE ATT&CK Mapping

**T1566 — Phishing**

The email used brand impersonation and a fraudulent reward lure to encourage recipient interaction.

A more specific sub-technique or successful execution was not established by the available evidence.

### 6. Assessment and Escalation

**Final Assessment:** High-confidence brand-impersonation phishing.

The sender identity mismatch, unrelated Return-Path, suspicious reward destination, and unusual HTML content support the classification.

Recommended SOC actions:

- Search the email gateway for other recipients.
- Identify and quarantine matching messages.
- Search proxy or web-filter logs for requests to the suspicious destination.
- Review EDR telemetry if recipient interaction is identified.
- Escalate if credential submission, suspicious downloads, or endpoint activity is discovered.

### 7. Conclusion

The investigation identified multiple indicators consistent with a brand-impersonation phishing attempt.

The sender used State Farm branding and a fraudulent Garmin Dash Cam reward to encourage interaction with an unrelated hosted page.

The appended HTML content was unusual and may have been intended to complicate automated analysis.

The email was classified as high-confidence phishing. No compromise was confirmed.

### 8. Evidence Reference

- [Original Phishing Email](evidence/01-original-phishing-email.jpg)
- [Email Header Analysis](evidence/02-email-headers.png)
- [HTML Branding and Links — Part 1](evidence/03-html-branding-and-links-1.png)
- [HTML Branding and Links — Part 2](evidence/03-html-branding-and-links-2.png)
- [HTML Content Padding — Part 1](evidence/04-html-content-padding-1.png)
- [HTML Content Padding — Part 2](evidence/04-html-content-padding-2.png)
- [WHOIS Sending IP Investigation — Part 1](evidence/05-whois-sending-ip-1.png)
- [WHOIS Sending IP Investigation — Part 2](evidence/05-whois-sending-ip-2.png)
