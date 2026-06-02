PHISHING INCIDENT ANALYSIS REPORT

1. INCIDENT OVERVIEW
   Incident ID: 006
   Date Detected: 18 May 2026
   Analyst: Hasan B.
   Severity: High
   Category: Phishing

2. EMAIL SUMMARY
   Subject: Urgent: Wire Transfer Needed
   Sender Display Name: CEO John Carter
   Sender Email: ceo@company-executive.com
   Recipient: finance@company.com
   Date Received: Wed, 15 April 2026 09:12:40
   Message ID: 99887766@company-executive.com

3. EXECUTIVE SUMMARY
   My assessment of this email is that it is Phishing. The phishing attempt is the sender 
(CEO John Carter - ceo@company-executive.com ) posing as the company CEO and sent a malicious email to the companies 
finance department requesting for an urgent wire transfer of exactly: $48,500. The sender 
 also specified that the wire transfer will  be sent to a "new venndor" and needs to be done 
in the next hour. The email shows consistency with phishing/spoofing due to the CEO email domain & the company finance 
department email domain does not match. The authentification of the email failed as well.  

4. TECHNICAL ANALYSIS

4.1 Header Authentication Results
SPF: Fail
DKIM: None 
DMARC: Fail

Analysis:
The failure of SPF and DMARC, combined with the absence of DKIM, indicates the sender is not
authorized to send emails on behalf of the domain

4.2 Email Routing (Received Chain)
Originating IP: 45.77.88.120
Relay IP(s):

Analysis:
[Explain where the email originated from and whether it is trustworthy.]

4.3 Domain Analysis
Sender Domain: ceo@company-executive.com
Observed Technique (if any):

Analysis:
[Explain if the domain is legitimate, spoofed, or suspicious.]

4.4 URL Analysis
Malicious URL(s):

Analysis:
[Explain what the URL does or is intended to do.]

4.5 Attachment Analysis (if applicable)
File Name:
File Type:
Hash (SHA256):

Analysis:
[Explain what the file contains and whether it is malicious.]

5. INDICATORS OF COMPROMISE (IOCs)

Indicator Type: Company domains don't match
Value: sender( ceo@company-executive.com ) / receiver (finance@company.com)

Indicator Type: Fail Authentification
Value: SPF: Fail / DKIM: None / DMARC: Fail 

Indicator Type: 
Value:

Indicator Type:
Value:

6. THREAT ASSESSMENT
   Threat Type:
   Confidence Level:

## Potential Impact:

*
*

7. BEHAVIORAL ANALYSIS

*
*
*

8. CONCLUSION
   [Provide your final determination: phishing, suspicious, or legitimate, with reasoning.]

9. RECOMMENDATIONS

*
*
*
*

10. EVIDENCE (OPTIONAL)

*
*
*
*
