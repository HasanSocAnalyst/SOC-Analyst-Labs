# SOC INCIDENT REPORT – NETWORK TRAFFIC ANALYSIS

## 1. Incident Overview

- **Incident ID:** CASE001
- **Analyst:** Hasan B.
- **Environment:** Lab Capture
- **Detection Source:** PCAP Analysis

---

## 2. Threat Classification

- **Category:** Network Traffic Investigation (Normal Activity Observed)
- **Severity:** Low
- **Confidence:** High

---

## 3. Executive Summary

Network traffic analysis identified normal endpoint activity consisting of DNS queries, 
TLS-encrypted communications, QUIC sessions, SSDP discovery traffic, ICMP echo requests, 
and peer-to-peer (P2P) communications over UDP port 6881. 
The P2P traffic is consistent with BitTorrent peer discovery and data exchange behavior. 
No evidence of malware, command-and-control (C2) communication, phishing activity, 
or data exfiltration was identified within the analyzed packet capture.

---

## 4. Network Traffic Summary

- **Protocols Observed:**
  - DNS
  - UDP
  - TCP
  - TLS 1.2
  - QUIC
  - SSDP
  - ICMP

- **Key Ports Observed:**
  - UDP/6881 (Peer-to-Peer)
  - TCP/443 (HTTPS)
  - UDP/443 (QUIC)

- **Traffic Pattern:**
  - DNS lookups to legitimate domains
  - Encrypted HTTPS and QUIC communications
  - Local network SSDP discovery traffic
  - Peer-to-peer communications over UDP port 6881
  - No sustained beaconing or abnormal connection intervals observed

---

## 5. Indicators Observed

- **Internal Host:** Redacted
- **Gateway:** Redacted
- **External Infrastructure:**
  - Cloudflare CDN
  - Google Services
  - Multiple external BitTorrent peers (Redacted)

- **Domains Observed:**
  - www.canva.com
  - beacons.gcp.gvt2.com
  - ogads-pa.clients6.google.com

- **Ports Observed:**
  - UDP/6881
  - TCP/443
  - UDP/443

- **Malicious Indicators:** None Identified

---

## 6. Detailed Analysis

The packet capture shows normal endpoint behavior involving encrypted web communications alongside peer-to-peer networking activity.
 DNS queries resolved legitimate domains before encrypted TLS and QUIC sessions were established with Google and Cloudflare infrastructure.

Several UDP conversations utilizing port 6881 indicate BitTorrent peer discovery and communication with multiple external peers.
 This decentralized communication pattern is characteristic of legitimate BitTorrent protocol behavior rather than centralized command-and-control (C2) infrastructure.

Additional network activity included SSDP multicast discovery requests, ICMP echo requests and replies, DNS resolution, and encrypted application traffic.
 No suspicious payloads, malicious domains, credential exposure, data exfiltration, or periodic beaconing behavior were observed during analysis.

---

## 7. Findings

Analysis determined that the captured traffic primarily consists of legitimate encrypted network communications combined with BitTorrent peer-to-peer activity.

Although BitTorrent is not inherently malicious, its use can increase organizational security risk through uncontrolled file sharing and potential exposure to malicious downloads.
 No evidence of malware execution, phishing activity, ransomware, command-and-control communication, or active compromise was identified within this packet capture.

---

## 8. Recommendations

- Review whether peer-to-peer applications are authorized within the environment.
- Monitor or restrict UDP port 6881 if BitTorrent traffic violates organizational policy.
- Continue monitoring endpoint traffic for unusual outbound connections or sustained beaconing behavior.
- Verify downloaded files originate from trusted sources.
- Maintain updated endpoint protection, IDS/IPS signatures, and network monitoring solutions.

---

## 9. Conclusion

The analyzed packet capture represents normal endpoint activity consisting of encrypted web communications,
 DNS resolution, SSDP discovery traffic, ICMP connectivity testing, and BitTorrent peer-to-peer networking. 
No indicators of malware infection, command-and-control communication, phishing activity, or data exfiltration were identified. 
While the observed P2P activity is not inherently malicious, it should be monitored in accordance with organizational security policies and acceptable-use guidelines.

---

## 10. Analyst Skills Demonstrated

- Packet inspection using Wireshark
- Protocol identification and analysis
- DNS traffic analysis
- TLS 1.2 analysis
- QUIC traffic analysis
- Peer-to-Peer (BitTorrent) traffic identification
- Network behavior analysis
- Risk assessment
- IOC identification
- Incident documentation and reporting
