SOC INCIDENT REPORT – NETWORK TRAFFIC ANALYSIS

1. Incident Overview
- Incident ID: CASE001
- Analyst: Hasan B
- Environment: Lab Capture
- Detection Source: PCAP Analysis

2. Threat Classification
- Category: Peer-to-Peer (P2P) Traffic
- Severity: Medium
- Confidence: High

3. Executive Summary
Network traffic analysis revealed significant UDP communication on port 6881 between an internal host (192.168.1.6) and multiple external IPv6 addresses. The traffic pattern indicates peer-to-peer file sharing activity consistent with BitTorrent protocol behavior. While not inherently malicious, such activity introduces security risks due to uncontrolled file transfers.

4. Network Traffic Summary
- Protocols Observed: UDP, TCP, TLS, ICMPv6
- Key Port: 6881 (BitTorrent)
- Pattern: High-volume peer communication across multiple external hosts

5. Indicators of Interest
- Internal IP: 192.168.1.6
- External IPs: Multiple (IPv6 peers)
- Ports: 6881 (primary)

6. Detailed Analysis
Traffic shows repeated UDP communication on port 6881, commonly associated with BitTorrent. Multiple external hosts initiate and respond to requests, indicating peer discovery and file-sharing behavior. Packet patterns and frequency confirm decentralized communication typical of P2P networks.

7. Findings
The analyzed traffic is consistent with BitTorrent-based peer-to-peer file sharing. No direct evidence of malware was identified; however, the activity increases exposure to potential malicious file downloads.

8. Recommendations
- Restrict or monitor P2P traffic on the network
- Block port 6881 if not required
- Educate users on risks of file sharing
- Monitor for suspicious downloads

9. Conclusion
The traffic represents non-malicious but potentially risky peer-to-peer activity. Continued monitoring is recommended.
