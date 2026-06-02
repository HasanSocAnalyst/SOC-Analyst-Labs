Case ID: 001 
Type: Phishing
Analyst: Hasan B


Summary:
A user received a suspicious email claiming urgency from Paypal and stating that they were unable to process the recent payment. And the user account would  be temporarily restricted if they didn't act fast. 

Findings(IOC):
- Sender Email: support@secure-payments-alert.com 
- Malicious Domain: http://secure-payment-update.com/login
- Suspicious IP: Hidden IP / checked both associated domains on VirusTotal
- Log Evidence:
- VirusTotal: Both domains (support@secure-payments-alert.com & http://secure-payment-update.com/login) came back with 0/95 scores 

Analysis:
The phishing email attempted to trick the user into urgency by claiming to temporarily restrict the user from accessing their Paypal acount.
The Phishing email also included an HTTP link to encourage users to click the link and update their payment info within 24 hours or it will result in account suspension. 
IP addresses are hidden on both domains
Domains not assocaited with actual company(PayPAl)

Conclusion:
This activity is high-level phishing email because the body text act as Paypal but the email account & domains have no related paypal domains to prove its association.

Recommendation:
- Block email domain secure-payments-alert.com
- Educate user on phishing awareness
