# Case-003 — State Farm Garmin Dash Cam Reward Phishing

**Case Type:** Email Phishing Investigation  
**Classification:** Brand-Impersonation Phishing  
**Severity:** High-confidence phishing attempt  
**Status:** Completed  
**Evidence Source:** Real unsolicited email received through Gmail

## Investigation Summary

Investigated an unsolicited email impersonating State Farm and claiming the recipient had won a Garmin Dash Cam reward.

The investigation examined email headers, sender infrastructure, embedded URLs, and HTML content. Multiple inconsistencies supported a high-confidence phishing classification.

## Key Findings

- Display name impersonated State Farm, but the sender domain was `cuzopyhwz.us`.
- Return-Path used an unrelated `coffeesforacause.com` subdomain.
- SPF passed for the Return-Path domain; this did not authenticate the claimed State Farm identity.
- No DKIM signature was present in the supplied headers; DMARC status was not reported.
- Sending IP `217.182.128.98` was associated with OVH SAS infrastructure in France.
- Reward and unsubscribe links both pointed to an HTML page hosted at `storage.googleapis.com`.
- The email contained 428 lines of unrelated content after the closing HTML document.
- No malware execution, credential submission, or account compromise was confirmed.

## Evidence

Original Phishing Email

Email Header Analysis

- [Original Phishing Email](evidence/01-original-phishing-email.jpg)
- [Email Header Analysis](evidence/02-email-headers.png)
- [HTML Branding and Links — Part 1](evidence/03-html-branding-and-links-1.png)
- [HTML Branding and Links — Part 2](evidence/03-html-branding-and-links-2.png)
- [HTML Content Padding — Part 1](evidence/04-html-content-padding-1.png)
- [HTML Content Padding — Part 2](evidence/04-html-content-padding-2.png)
- [WHOIS Sending IP Investigation — Part 1](evidence/05-whois-sending-ip-1.png)
- [WHOIS Sending IP Investigation — Part 2](evidence/05-whois-sending-ip-2.png)
  
## Disposition

Classified as a high-confidence brand-impersonation phishing attempt using a fraudulent reward lure.

The unrelated HTML content may represent content padding intended to complicate automated analysis or influence filtering. This purpose was not confirmed.

No compromise was confirmed. The destination page was not opened.

## Skills Demonstrated

- Email header analysis
- SPF and email authentication interpretation
- Sender domain and Return-Path analysis
- WHOIS and IP ownership investigation
- URL and HTML source inspection
- Phishing identification and classification
- Evidence-based incident assessment

[Read the full investigation report](analyst_report.md)
