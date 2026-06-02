# SOC INCIDENT REPORT – NETWORK TRAFFIC ANALYSIS

## 1. Incident Overview
- Incident ID: 003
- Date/Time (UTC):
- Analyst: Hasan B.
- Environment: (Lab / Production Simulation)
- Detection Source: (PCAP / Alert / Email / IDS)

## 2. Threat Classification
- Category: (Phishing / Malware / C2 / Data Exfiltration / Reconnaissance)
- Severity: (Low / Medium / High / Critical)
- Confidence Level: (Low / Medium / High)

## 3. Executive Summary
Brief 3–5 sentence summary:
- What happened
- How it was identified
- Impact level
- Recommended action

## 4. Network Traffic Summary
- Total Packets Analyzed:
- Time Range:
- Protocols Observed: (HTTP, DNS, TCP, TLS, ICMP, etc.)
- Suspicious Patterns Identified:
  - Unusual ports
  - Beaconing behavior
  - Large outbound transfers
  - Repeated failed connections

## 5. Indicators of Compromise (IOCs)
- Source IP:
- Destination IP:
- Domain(s):
- URL(s):
- File Hashes (if applicable):
- User-Agent Strings:
- JA3/JA3S (if TLS analysis done):

## 6. Detailed Analysis

### 6.1 Traffic Behavior
- Connection patterns (normal vs abnormal)
- Frequency/timing (beaconing intervals?)
- Protocol misuse

### 6.2 Packet Inspection Findings
- Suspicious payloads
- Encoded/obfuscated data (Base64, etc.)
- Credentials or sensitive data exposure

### 6.3 DNS Analysis
- Suspicious domains
- Newly registered domains
- Domain entropy (random-looking strings)

### 6.4 HTTP/HTTPS Analysis
- Malicious URLs
- File downloads
- Suspicious headers

## 7. Tools & Methodology
- Wireshark (packet inspection, filtering)
- Tshark (CLI extraction)
- tcpdump (capture/quick filtering)
- NetworkMiner (artifact extraction)
- VirusTotal (IOC validation)
- URLScan (web analysis)

## 8. Investigation Steps
1. Loaded PCAP into Wireshark
2. Applied protocol filters (dns, http, tcp.stream)
3. Identified abnormal traffic patterns
4. Extracted suspicious IPs/domains
5. Validated IOCs using OSINT tools
6. Reconstructed sessions (if applicable)

## 9. Findings
- Clear statement of what was malicious
- How it behaved
- Why it is malicious (this is KEY for employers)

## 10. Mitigation & Recommendations
- Block IP/domain at firewall
- Isolate affected host
- Monitor for similar traffic patterns
- Update IDS/IPS signatures

## 11. Conclusion
Short, confident closing statement summarizing the threat and response.

## 12. Evidence (Screenshots)
- Wireshark packet view
- Follow TCP stream
- DNS queries
- Suspicious payloads
