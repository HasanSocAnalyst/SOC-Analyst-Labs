
PHISHING INCIDENT ANALYSIS REPORT

1. INCIDENT OVERVIEW
   Incident ID: 005
   Date Detected: 
   Analyst: Hasan B.
   Severity: High
   Category: Phishing - Social Engineering / Spear Phishing 

2. EMAIL SUMMARY
   Subject: Urgent: Suspicious Activity Detected
   Sender Display Name: PayPal Security
   Sender Email: security@paypaI.com
   Recipient: employee@company.com
   Date Received: Mon, 10 May 2026 15:22:08
   Message ID: ABCD1234@mail.paypaI.com

3. EXECUTIVE SUMMARY
   this report analyzes a suspicious email received by an employee and is identified as a phishing
attempt impersonating a company(PayPal). The email attempts to urgently encourage the employee
to click a malicious link(http://paypal.verify-user-login.com/security-check) or their paypal
account will be suspended. The link has a VirusTotal score of 5/91 and has been flagged as
suspicious and fraud via VirusTotal. There are 2  different domains associated within the header of the 
email: security@paypaI.com , mail.paypaI.com.  

4. TECHNICAL ANALYSIS

4.1 Header Authentication Results
SPF: Pass
DKIM: Pass
DMARC: Pass

Analysis:
SPF/DKIM/DMARC all passed authentification check

4.2 Email Routing (Received Chain)
Originating IP: 203.0.113.77

Analysis: the IP does not have malicious activity via ViruaTotal (0/91 score). The IP is 
associated with the domain mail.paypaI.com (Virustotal: 0/91 score)


4.3 Domain Analysis
Sender Domain: paypai.com 
Observed Technique (if any): The sender of this email is using "PayPal" to try to trick the 
employee by using an "I" instead of an "l" onb the domain 

Analysis:
the domain "paypaI.com" is crafted using an "I" while at the same time encouraging the employee 
to "immediately" take action and click the link within the body of thew email

4.4 URL Analysis
Malicious URL(s): http://paypal.verify-user-login.com/security-check

Analysis:
the link attached to the email body is malicious. The URL starts with http, doesn't match PayPal
 company URL's, the domain is not the same domain as the sender domain(paypaI.com), and the URL
has been flagged on virustotal: 5/91 (BitDefender/ESET/Fortinet/G-Data/Sophos) / Sophos clarified:
Phishing & Fraud 

4.5 Attachment Analysis: there are attachments with this email



5. INDICATORS OF COMPROMISE (IOCs)

Indicator Type: Fraudulent Domain
Value: PaypaI.com

Indicator Type: Malicious Body URL
Value: http://paypal.verify-user-login.com/security-check

Indicator Type: Malicious Sender & Return domain
Value: security@paypaI.com


6. THREAT ASSESSMENT
   Threat Type: Spear Phishing / Social Engineering
   Confidence Level: High

## Potential Impact:

* Employee clicks malicicious link and downloads Malware to the company Network
* If link is clicked threat actor can access confidential information

7. BEHAVIORAL ANALYSIS

* Urgency: Impersonating Paypal to encourage employee to immediately click the link
* Deceptive Fraud Domain: PayPai.com
* Senders domain does not match malicous domain
* This is no IP connected to the body malicious URL, that indicates its not a legit URL and is 
mainly used to upload Malware

8. CONCLUSION
   Based on my findings this email is confirmed as a phishing attempt. The threat actor trys to 
 impersonate PayPal to encourage employees to click a link and possibly download Malware to the
company network, or infiltrat confidential information.

9. RECOMMENDATIONS

* Block malicious domain at the network level
* Conduct employee training 
* Monitor for similar phishing attemps

