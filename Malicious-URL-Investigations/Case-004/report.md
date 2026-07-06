========================================
INCIDENT REPORT – PHISHING ANALYSIS
========================================

Incident ID: CASE-005
Date: 2026-04-27
Analyst: Hasan B.

----------------------------------------
1. OVERVIEW
----------------------------------------

Threat Type: Phishing / Credential Harvesting / Scam
Severity: [Low / Medium / High]
Confidence Level: [Low / Medium / High]

Summary:
A suspicious website was identified exhibiting characteristics consistent with [phishing / credential harvesting / financial scam]. The site presents a [login interface / lure theme] and is designed to [harvest credentials / redirect users / facilitate fraud].

----------------------------------------
2. INDICATORS OF COMPROMISE (IOCs)
----------------------------------------

Domain(s):
- ledgermobile.com

URL(s):
- https://ledgermobile.com/

IP Address(es):
- VirusTotal: 18.208.88.157 ### very suspicious
- Command: dig +short = 13.215.239.219 / 52.74.6.109
- URLscan.io: 63.176.8.218

ASN / Hosting:
- AS16509 (Amazon.com,Inc., US)

External Links:
- https://t.me/ledgermobile
- 
- [Any other domains]

----------------------------------------
3. ANALYSIS
----------------------------------------

3.1 Domain & Registration:
- Domain creation date: 2026-02-12
- Registrar / WHOIS: whois.name.com
- Domain age assessment:  Recently registered

3.2 Website Behavior:
- Credential harvesting interface observed (e.g., login form)
- Form fields identified: [email / password / other]
- Form submission behavior: [POST request / unknown / not observed]
- Page intent: [impersonation / financial lure / unclear]

3.3 Infrastructure:
- Hosting IP: [IP address]
- Location: [Country]
- Shared hosting observed: [# of domains if known]
- Related domain(s): [if applicable]

3.4 Network & Traffic Behavior:
- Redirect chain observed:
  [IP → domain → final URLx]
- HTTP response codes: 200
- Use of CDN / protection services (e.g., Cloudflare): [Yes/No]

3.5 External Communication:
- Outbound connections identified:
  - [Telegram / API / unknown domains]
- Purpose:
  - Potential data exfiltration / attacker-controlled communication

3.6 Security Evasion Techniques:
- CAPTCHA / anti-bot mechanisms (e.g., Cloudflare Turnstile)
- Obfuscation / script loading behavior
- Low detection rate across security vendors

----------------------------------------
4. TECHNICAL FINDINGS
----------------------------------------

- Login/credential input fields present
- [POST request observed / Not observed]
- Redirect behavior consistent with traffic masking
- External communication to attacker-controlled platform (if applicable)
- Infrastructure indicates [shared hosting / suspicious region / mixed services]

----------------------------------------
5. EVIDENCE (SCREENSHOTS)
----------------------------------------

Figure 1: URLScan screenshot showing login interface and page title
Figure 2: VirusTotal URL analysis (4/91 detections) 
Figure 3: VirusTotal IP analysis (0/95 flagged) /  
Figure 4: URLScan form analysis (HTML login form)
Figure 5: Redirect chain and infrastructure mapping

[Attach screenshots in order OR reference file names]

----------------------------------------
6. RISK ASSESSMENT
----------------------------------------

Risk Level: [Low / Medium / High]

Justification:
- Presence of credential harvesting interface
- Suspicious domain characteristics
- External communication channel detected
- Financial or social engineering lure identified
- Limited detection suggesting potential evasion

----------------------------------------
7. CONCLUSION
----------------------------------------

The analyzed website demonstrates multiple indicators consistent with [phishing / credential harvesting / scam activity]. While [no direct evidence of credential exfiltration was observed], the combination of behavioral, infrastructural, and contextual indicators suggests a high likelihood of malicious intent.

----------------------------------------
8. RECOMMENDATIONS
----------------------------------------

- Block domain(s) and IP address(es) at DNS, firewall, and proxy levels
- Monitor for additional domains associated with the same infrastructure
- Add identified indicators to threat intelligence platforms
- Investigate potential user interaction within the environment
- Report domain to hosting provider and relevant abuse channels

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
