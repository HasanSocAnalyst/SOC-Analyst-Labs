# SOC INCIDENT REPORT – NETWORK TRAFFIC ANALYSIS

## 1. Incident Overview
- Incident ID: 002
- Date/Time (UTC): 28 March 2026
- Analyst: Hasan B.
- Environment: Lab
- Detection Source: PCAP Analysis 

## 2. Threat Classification
- Category: Peer 2 Peer
- Severity: Medium
- Confidence Level: High

## 3. Executive Summary
Nertwork Traffic analysis revealed a high amount of TCP communication on port 443 between the internal IP(192.168.1.193) and multiple external IPV6 addresses. The traffic pattern is consistent with regular behavior. No malicioius activity that will cause a security risk or threat. 

## 4. Network Traffic Summary
- Protocols Observed: DNS, TCP, TLS, ICMP

## 5. Indicators of Compromise (IOCs)
- Source IP: 192.168.1.193 
- Destination IP: Multiple (IPv6 peers)
- Port: 443 (Primary)

## 6. Detailed Analysis

### 6.1 Traffic Behavior
- Total Packets: 23k
- Capture Duration: 21.6 seconds
- SRC IP: 192.168.1.193 | Internal Host
- Unique DST: 47 external IPs | multiple peers
- Primary Port: 443 (HTTPS) | encrytped transport
- Avg Packet Size: 1101.56 bytes


### 6.2 Packet Inspection Findings
- No visible HTTP requests 
- TLS handshake show no Server Name Indication (SNI)
- Noi credentials, base64 strings, or plaintext data observed

### 6.3 DNS Analysis
- Suspicious domains
- Newly registered domains
- Domain entropy (random-looking strings)

### 6.4 HTTP/HTTPS Analysis
- there was no visible malicious activity or files downloaded

## 7. Tools & Methodology
- Wireshark (packet inspection, filtering)
- Tshark (CLI extraction)
- tcpdump (capture/quick filtering)
- VirusTotal (IOC validation)
- URLScan (web analysis)

## 8. Investigation Steps
1. Loaded PCAP into Wireshark
2. Extracted the file on Tshark
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

