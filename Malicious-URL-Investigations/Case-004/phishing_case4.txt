========================================
INCIDENT REPORT – PHISHING ANALYSIS
========================================

Incident ID: CASE-004
Date: 2026-04-11
Analyst: Hasan B.

----------------------------------------
1. OVERVIEW
---------------------------------------
Threat Type: Phishing / Credential Harvesting / Sca
Severity: High
Confidence Level: High

Summary:
A suspicious website was identified exhibiting characteristics consistent with Phishing.
The site presents 2 redirects and a hidden domain in the header(nouvelle-carte-biometrique.com)
Once a user access page, lockrcxvd.com they are redirected to nouvelle-carte-biometrique.com (hidden) 
then redirects again to www.mediapart.fr which is the final destination.
Inside the header of pages: lockrcxvd.com & www.mediapart.fr, there is a linux/Mozilla command: 
User-Agent": "Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) 
Chrome/147.0.0.0 Safari/537.36"
The setup is suspicius as well: IP location: Pakistan / 
www.mediapart.fr IP Location: USA(151.101.194.132 URLscan.io / 199.232.166.132 Command: 
dig +short www.mediapart.fr) / 
Final website destination language: French.. each has a different global location
 
----------------------------------------
2. INDICATORS OF COMPROMISE (IOCs)
----------------------------------------

Domain(s):
- lokrcxvd.com/

URL(s):
- https://lokrcxvd.com/

IP Address(es):
- 180.178.160.59

ASN / Hosting:
- AS213441 - SLAYER-AS SLAYER GROUP LIMITED, GB

External Links:
- 
- 

----------------------------------------
3. ANALYSIS
----------------------------------------

3.1 Domain & Registration:
- Domain creation date: 2026-04-08
- Registrar / WHOIS: whois.registrar.eu
- Domain age assessment: New
- Name Servers: NS1.OPENPROVIDER.NL, NS2.OPENPROVIDER.BE, NS3.OPENPROVIDER.EU

3.2 Website Behavior:
- lokrcxvd.com redirects to another URL (www.mediapart.fr)
- Page intent: download virus from header using Linux commands( see image:
## ~/SOC_Lab/Phishing_Analysis/Phishing_Links/Case4/Images/case4_URLscan4API.png 

3.3 Infrastructure:
- Hosting IP: 151.101.66.132
- Location: USA
- Shared hosting observed: 228 hits for the same IP but different domains 
- Related domain(s): www.mediapart.fr / nouvelle-carte-biometrique.com

3.4 Network & Traffic Behavior:
- Redirect chain observed:
  180.178.160.59 → lokrcxvd.com → nouvelle-carte-biometrique.com → www.mediapart.fr
https://lokrcxvd.com/- HTTP response codes: 200
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
Figure 2: VirusTotal URL analysis (3/95 detections) 
Figure 3: VirusTotal IP analysis (2/95 flagged) 
Figure 4: URLScan form analysis (HTML login form)
Figure 5: Redirect chain and infrastructure mapping

[Attach screenshots in order OR reference file names]

## Location: ~/SOC_Lab/Phishing_Analysis/Phishing_Links/Case4/Images/
case4_URLscan1.png  case4_URLscan3.png      case4_VirusTotal1.png  case4_VirusTotal3.png
case4_URLscan2.png  case4_URLscan4_API.png  case4_VirusTotal2.png

----------------------------------------
6. RISK ASSESSMENT
----------------------------------------

Risk Level: High

Justification:
- Suspicious domain characteristics
- Limited detection suggesting potential evasion

----------------------------------------
7. CONCLUSION
----------------------------------------

The analyzed website demonstrates multiple indicators consistent with phishing. While no direct evidence of credential exfiltration was observed, 
the combination of behavioral, infrastructural, and contextual indicators suggests a high likelihood of malicious intent. 
Hidden domains with different IPs and locations all indicate highlevel phishing

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
