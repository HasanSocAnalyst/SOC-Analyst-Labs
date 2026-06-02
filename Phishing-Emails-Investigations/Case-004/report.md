PHISHING INCIDENT ANALYSIS REPORT

1. INCIDENT OVERVIEW
   Incident ID: 004
   Date Detected: 2026-10-04
   Analyst: Hasan B.
   Severity: High 
   Category: Phishing/Credential Harvesting

2. EMAIL SUMMARY
   Subject: Quick Confirmation Needed 
   Sender Display Name: Michael Johnson
   Sender Email: m.johnson@company-support.com 
   Recipient: employee@company.com
   Date Received: Thu, 02 Apr 2026 17:15:28
   Message ID: CAEPk3Z2abc123@mail.company-support.com

3. EXECUTIVE SUMMARY
   This report analyzes a suspicious email identified as a phishing attempt 
   impersonating a company employee from the support department. 
   The message attempts to deceive an employee to send a reply message 
   with their updated contact information. There is a hidden IP(026.04.02.10)
   within the header that has a probable malicious MS Word Doc attached
   name: LATEST DTMS_VOLUME II_TECHNICAL SPECIFICATIONS_LATEST 08th NOV 2021.doc.
   The file has been flagged malicious with a score of  1/50 (ASP.Webshell)
   via VirusTotal. 
   The employee domain(company.com) and suspected phishing domain(company-support.com) is not the same
   which is a clear indication of malicious phishing activity. 
    

4. TECHNICAL ANALYSIS

4.1 Header Authentication Results
SPF: Pass
DKIM: Pass
DMARC: Pass

Analysis:
 SPF/DKIM/DMARC all passed authentification check.

4.2 Email Routing (Received Chain)
Originating IP: 198.51.100.23
Relay IP(s): 026.04.02.10

Analysis:
The sender and return path IP is the same. 
There is a hidden IP(026.04.02.10) with no domain connected.
This is a clear indication of phishing and credential harvesting
because of the senders request to retreive more of victim personal information.  

4.3 Domain Analysis
Sender Domain: company-support.com 
Observed Technique (if any):domain indicated "company support" 
while urgently instructing victim to update personal info. 
Both sender & returning IP's are the same. But the employee domain is different(company.com) which 
is a clear indicator of phishing activity.

Analysis:
The domain is created with the words "company-support" with efforts to trick
users/victims to send personal info beleiving its a company-based email

4.4 URL Analysis
Malicious URL(s): no existing URL in header/body of email


4.5 Attachment Analysis (if applicable)
File Name:LATEST DTMS_VOLUME II_TECHNICAL SPECIFICATIONS_LATEST 
File Type: MS Word Doc

Analysis:


5. INDICATORS OF COMPROMISE (IOCs)

Indicator Type: hidden IP 026.04.02.10
Value: hidden in Email header

Indicator Type: Malicious domains
Value: company-support.com

Indicator Type: Sense of Urgency
Value: "Quick Confirmation Needed"


6. THREAT ASSESSMENT
   Threat Type: Phishing Social Engineering / Credential Harvesting 
   Confidence Level: High

## Potential Impact:

* Threat Actor obtains valuable employee information
* Phishing attempts could get valuable company info

7. BEHAVIORAL ANALYSIS

* The threat actor is attempting to harvest credentials & personal info
* By sending employees an email to update personal info and reply back to the same email address
* Once employee replies their information is harvested 

8. CONCLUSION
   [Provide your final determination: phishing, suspicious, or legitimate, with reasoning.]

9. RECOMMENDATIONS

* Block email Ip
* Block Email Domain
* Educate Users
*

10. EVIDENCE (OPTIONAL)

* Sender and receiving domains don't match
* Hidden IP in header
* Malicious MS Word Doc file connected to hidden IP
* request for "Urgent" response
