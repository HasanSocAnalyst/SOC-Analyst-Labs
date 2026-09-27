# Analyst Report — Meta Trusted-Account Phishing  
  
## Incident Summary  
  
On 22 September 2026 at 17:41, a suspicious "Meta Alert" was received  
through an established Facebook Messenger conversation with a known contact.  
  
The message claimed account violations, threatened account disablement  
within 24 hours, and requested account verification through an attached  
PDF: `Facebook_Support_Center_2026.pdf` (155 KB).  
  
The PDF was not opened or analyzed.  
  
## Investigation  
  
The message displayed several phishing characteristics:  
  
- Meta/Facebook support impersonation  
- Artificial 24-hour urgency  
- Account-verification request  
- PDF attachment  
- Delivery through a trusted contact's Messenger account  
  
The legitimate account owner was contacted through a separate trusted  
channel and confirmed that he did not send the message.  
  
Previous legitimate conversations were present in the same Messenger  
thread, supporting unauthorized use of the legitimate account.  
  
When the sender profile was accessed, Facebook displayed  
"This Content Isn't Available." The reason for the profile being  
unavailable could not be determined.  
  
## MITRE ATT&CK  
  
**Tactic:** Initial Access    
**Technique:** T1566 — Phishing    
**Sub-technique:** T1566.003 — Spearphishing via Service  
  
The phishing lure was delivered through Facebook Messenger, a  
third-party social-media service.  
  
## Evidence & Artifacts  
  
- Original phishing-message screenshot  
- Sender-profile unavailable screenshot  
- Independent sender verification  
- Existing legitimate conversation history  
- `Facebook_Support_Center_2026.pdf` — 155 KB (not analyzed)  
  
**Technical IOCs:** None confirmed.  
  
## Containment  
  
- Suspicious PDF was not opened or downloaded  
- Evidence was preserved before reporting  
- Legitimate account owner was independently notified  
- Recommended password reset, session review, MFA, and review of  
  recent outgoing messages  
  
## Final Assessment  
  
**Disposition:** Phishing    
**Confidence:** Very High    
**Attack Type:** Social Media Phishing / Trusted-Account Phishing    
**Account Status:** Currently inaccessible — reason unknown  
  
Evidence strongly supports unauthorized use of the legitimate Messenger  
account. The initial account-access method remains unknown.  
  
## Limitations  
  
The PDF was intentionally not acquired or opened on the analyst's personal  
device. File hashes, embedded URLs, domains, and other potential technical  
IOCs could therefore not be extracted.  
