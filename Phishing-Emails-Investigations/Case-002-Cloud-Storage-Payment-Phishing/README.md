# Case-002 — Cloud Storage Payment Phishing

**Investigation Type:** Email Phishing Analysis  
**Evidence Source:** Real Gmail Spam Email (.eml)  
**Tools:** Python, Email Headers, MIME Analysis  
**Classification:** Phishing — High Confidence  
**Severity:** Medium  
**MITRE ATT&CK:** T1566.002 — Phishing: Spearphishing Link

## Investigation Summary

Investigated a suspicious cloud-storage notification threatening account restrictions and deletion of photos and videos.

Analyzed email headers, SPF/DKIM authentication results, embedded URLs, and MIME structure to determine whether the message was legitimate.

## Key Findings

- **Subject:** Account blocked; photos and videos threatened with deletion.
- **Sender:** Unrelated sender and return-path domains.
- **Authentication:** SPF and DKIM passed for sender-controlled domains; legitimacy was not established.
- **Recipient:** Visible `To` address differed from the delivered mailbox.
- **URLs:** Five URLs across two hostnames, including an unverified cloud-hosted payment-update page.
- **Social Engineering:** Same-day deletion threat and urgent payment request.
- **MIME:** Three HTML parts; no attachment filenames or explicit attachment dispositions.
- **Impact:** No confirmed credential submission, payment theft, or compromise.

## Evidence

![Email Header Analysis](evidence/01-email-header-analysis.png)

![Suspicious URL Analysis](evidence/02-suspicious-url-analysis.png)

![Phishing Email Content](evidence/03-phishing-content.png)

## Disposition

**Phishing — High Confidence.**

The message used deceptive cloud-service branding, inconsistent sender identities, and an unverified payment-update link to encourage recipient interaction.

The suspected objective was payment-information harvesting. No successful compromise was established.

## Skills Demonstrated

Email header analysis · SPF/DKIM interpretation · URL extraction · MIME analysis · Social engineering detection · Phishing classification

[Read the full investigation report](analyst_report.md)
