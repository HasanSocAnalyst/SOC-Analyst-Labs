========================================
INCIDENT REPORT – PHISHING ANALYSIS
========================================

Incident ID: CASE-002
Date: 2026-03-29
Analyst: Hasan B.

----------------------------------------
1. OVERVIEW
----------------------------------------

Threat Type: Phishing Link
Severity: High
Confidence Level: High

Summary:
A suspicious website was identified exhibiting characteristics consistent with phishing.
After domain(crystalwheeler.com) is loaded a 404 message appears "the page you were looking for was not found". 
The IP address of : 43.153.182.147 has 20 domains connected to it(verified by url.io) and they all arrive at the same destination/page.
One of the main indicators that it is high level malicious activity because the domain was recently updated on 2026-03-23 
and has a 404 message across 20 different domains.
Inside the header the user-agent consist of Mozilla/5.0 (x11; Linux x86_64) 
Inside the Reponse Header contains a content-encoding of a "gzip" file which is a high indication of phishing 

----------------------------------------
2. INDICATORS OF COMPROMISE (IOCs)
----------------------------------------

Domain(s):
- crystalwheeler.com

URL(s):
- https://crystalwheeler.com/A36GiJR5Hq

IP Address(es):
- 43.153.182.147

ASN / Hosting:\
- AS132203 (Tencent-NET-AP-CN Tencent Building, China)

External Links:


----------------------------------------
3. ANALYSIS
----------------------------------------

3.1 Domain & Registration:
- Domain creation date: 2025-05-23
- Registrar / WHOIS: www.gname.com/whois
- Domain expiry date: 2026-05-23
- Name Servers: A3.SHARE-DNS.com | B3.SHARE_DNS.net
- Domain age assessment: recently updated

3.2 Website Behavior:
- Download virus to user CPU (404 Page Not Found)
- After user visit page it seems a virus is downloaded 
- Page intent: dsownload virus

3.3 Infrastructure:
- Hosting IP: 43.153.182.147
- Location: Japan
- Shared hosting observed: 20 domains with similar IP

3.4 Network & Traffic Behavior:
- Redirect chain observed:
  43.152.182.147 → www.crystalwheeler.com → https://crystalwheeler.com/A36GiJR5Hq
- HTTP response codes: 200
- Cloudflare): [Yes/No]

3.5 External Communication:
- Outbound connections identified:
  - API
- Purpose:
  - downloads gzip file

3.6 Security Evasion Techniques:
- CAPTCHA / anti-bot mechanisms (e.g., Cloudflare Turnstile)
- Obfuscation / script loading behavior
- Low detection rate across security vendors

----------------------------------------
4. TECHNICAL FINDINGS
----------------------------------------

- VirusTotal results:
 - URL: 19/95
 - IP: 0/95
----------------------------------------
5. EVIDENCE (SCREENSHOTS)
----------------------------------------

Figure 1: URLScan screenshot showing login interface and page title
Figure 2: VirusTotal URL analysis (0 detections)  
Figure 3: VirusTotal IP analysis (19/95 flagged) 
Figure 4: URLScan form analysis (HTML login form)
Figure 5: URLScan API

##ALL images are found: ~/SOC_Lab/Phishing_Analysis/Phish_Imgs

----------------------------------------
6. RISK ASSESSMENT
----------------------------------------

Risk Level: High level

Justification:
- 1 IP connected to many domains
- Suspicious domain characteristics
- gzip file detected in API

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
