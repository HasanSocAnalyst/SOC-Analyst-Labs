# Case-001 — Meta Trusted-Account Phishing  
  
## Overview  
  
A real-world phishing incident involving a Meta impersonation lure delivered  
through an established Facebook Messenger conversation with a known contact.  
  
The legitimate account owner independently confirmed that the message was  
unauthorized. The suspicious message attempted to create urgency by claiming  
account violations and threatening account disablement within 24 hours.  
  
## Key Findings  
  
- Phishing lure delivered through Facebook Messenger  
- Message originated from an established conversation with a known contact  
- Legitimate account owner confirmed the message was unauthorized  
- Meta/Facebook support was impersonated  
- Message requested account verification  
- Suspicious PDF attachment observed: `Facebook_Support_Center_2026.pdf`  
- Attachment was intentionally not opened or analyzed  
- Sender profile later displayed "This Content Isn't Available"  
- Reason for profile unavailability could not be determined  
  
## MITRE ATT&CK  
  
- Tactic: Initial Access  
- Technique: T1566 — Phishing  
- Sub-technique: T1566.003 — Spearphishing via Service  
  
## Classification  
  
**Disposition:** Phishing    
**Confidence:** Very High    
**Attack Type:** Social Media Phishing / Trusted-Account Phishing  
  
Evidence strongly supports unauthorized use of the legitimate Messenger  
account. The method of account access could not be determined.  
  
## Evidence  
  
- `01-original-phishing-message.PNG`  
- `02-sender-profile-unavailable.PNG`  
  
## Skills Demonstrated  
  
- Phishing triage  
- Social-engineering analysis  
- Evidence preservation  
- Incident scoping  
- MITRE ATT&CK mapping  
- Account-compromise assessment  
- Containment and remediation recommendations  
- Evidence-based incident classification  
