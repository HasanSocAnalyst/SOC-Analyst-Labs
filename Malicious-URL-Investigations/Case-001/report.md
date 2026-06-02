========================================
INCIDENT REPORT – PHISHING ANALYSIS
========================================

### ADD SCREENSHOTS PATH TO IMG ####

Incident ID: CASE-001
Date: 2026-03-23
Analyst: Hasan B

----------------------------------------
1. OVERVIEW
----------------------------------------

Threat Type: Suspicious / Credential Harvesting / Financial Scam
Severity: High
Confidence Level: Medium-High

Summary:
A suspicious website was identified promoting a cryptocurrency-based “passive income” platform. The site presents a login interface and redirects users to an external Telegram channel. Observed behavior is consistent with credential harvesting and financial scam activity.

----------------------------------------
2. INDICATORS OF COMPROMISE (IOCs)
----------------------------------------

Domain(s):
- energycycle.by

URL(s):
- https://energycycle.by/?ref=1281

IP Address(es):
- 93.125.99.151

ASN / Hosting:
- AS6697 (Beltelecom, Belarus)

External Links:
- https://t.me/energycycleby

----------------------------------------
3. ANALYSIS
----------------------------------------

3.1 Domain & Registration:
- Domain creation date: 2026-01-05
- Registrar: Reliable Software Ltd
- Name servers: ns1.hoster.by / ns2.hoster.by
- Expiration date: 2027-01-05
- Domain age assessment: Recently registered

3.2 Website Behavior:
- Credential harvesting interface observed (email input + login form)
- Form submission behavior not clearly identified
- User interaction leads to redirection to external Telegram channel
- Page theme promotes cryptocurrency-based passive income (common scam lure)

3.3 Infrastructure:
- Hosting IP: 93.125.99.151
- Location: Belarus
- Associated domain: start.hoster.by
- Shared hosting observed: 124 domains on same IP

3.4 Network & Traffic Behavior:
- Redirect chain observed:
  93.125.99.151 → start.hoster.by → energycycle.by
- HTTP response codes observed: 200, 302, 307, 403
- Cloudflare Turnstile CAPTCHA detected (anti-bot mechanism)

3.5 External Communication:
- Outbound link identified:
  https://t.me/energycycleby
- Use of Telegram suggests potential attacker-controlled communication or data exfiltration channel

3.6 Security Evasion Techniques:
- Cloudflare Turnstile CAPTCHA present
- Use of CDN (Cloudflare) to mask origin infrastructure
- Low detection rate across security vendors (VirusTotal)

----------------------------------------
4. TECHNICAL FINDINGS
----------------------------------------

- HTML login form detected with email input field
- No explicit form action identified in static analysis
- Redirect behavior consistent with traffic routing or masking
- External communication to Telegram platform observed
- Infrastructure indicates shared hosting environment in Belarus
- VirusTotal results:
  - URL: 0/95 detections
  - IP: 1/94 detections
- WGET request failed to resolve host (cause undetermined; possible DNS or environment-related issue)

----------------------------------------
5. EVIDENCE (SCREENSHOTS)
----------------------------------------

Figure 1: URLScan screenshot showing login interface and page title  
Figure 2: VirusTotal URL analysis (0 detections)  
Figure 3: VirusTotal IP analysis (1/94 flagged)  
Figure 4: URLScan form analysis showing HTML login structure  
Figure 5: URLScan summary showing redirect chain and infrastructure  

----------------------------------------
6. RISK ASSESSMENT
----------------------------------------

Risk Level: High

Justification:
- Credential harvesting interface present
- Cryptocurrency-based financial lure identified
- External communication channel (Telegram) detected
- Shared hosting with multiple domains increases risk exposure
- Low detection rate suggests possible evasion or newly active infrastructure

----------------------------------------
7. CONCLUSION
----------------------------------------

The analyzed website demonstrates multiple indicators consistent with credential harvesting and financial scam activity. While no direct evidence of credential exfiltration was confirmed, the presence of a login interface, Telegram redirection, and cryptocurrency-based incentives strongly suggests malicious intent.

----------------------------------------
8. RECOMMENDATIONS
----------------------------------------

- Block domain and IP at DNS, firewall, and proxy levels
- Monitor for additional domains resolving to 93.125.99.151
- Add identified indicators to threat intelligence platforms
- Investigate potential internal user interaction with the domain
- Report domain and associated infrastructure to hosting provider

----------------------------------------
9. TOOLS USED
----------------------------------------

- PhishTank
- VirusTotal
- URLScan.io
- whois
- dig
- curl / wget

========================================
END OF REPORT
========================================
