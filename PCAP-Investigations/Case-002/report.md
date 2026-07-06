# SOC INCIDENT REPORT – NETWORK TRAFFIC ANALYSIS

## 1. Incident Overview

- **Incident ID:** CASE002
- **Analyst:** Hasan B.
- **Environment:** Home Lab Capture
- **Detection Source:** PCAP Analysis

---

## 2. Threat Classification

- **Category:** Peer-to-Peer (P2P) Network Activity Investigation
- **Severity:** Low
- **Confidence:** High

---

## 3. Executive Summary

Analysis of the packet capture identified normal network activity consisting of DNS resolution, TLS 1.2 encrypted communications, QUIC traffic, SSDP service discovery, mDNS device discovery, and peer-to-peer (P2P) communications over UDP port 6881. The observed P2P traffic is consistent with legitimate BitTorrent peer discovery and file-sharing behavior. Additional traffic included connections to Google infrastructure, Cloudflare-hosted services, and Google Video content delivery. No evidence of malware, phishing, command-and-control (C2) communications, or data exfiltration was identified during the investigation.

---

## 4. Network Traffic Summary

### Protocols Observed

- DNS
- mDNS
- SSDP
- UDP
- TCP
- TLS 1.2
- QUIC
- ICMP

### Significant Ports

- UDP/6881 (BitTorrent Peer-to-Peer)
- TCP/443 (HTTPS)
- UDP/443 (QUIC)

### Traffic Characteristics

- Multiple DNS lookups for legitimate Google services
- Encrypted HTTPS communications
- QUIC sessions to Google infrastructure
- Local multicast discovery traffic (SSDP and mDNS)
- Multiple peer-to-peer communications over UDP port 6881
- No periodic beaconing behavior observed
- No excessive outbound data transfers observed

---

## 5. Indicators Observed

### Internal Assets

- Internal Host: **Redacted**
- Default Gateway: **Redacted**

### External Infrastructure

- Google Services
- Google Video CDN
- Cloudflare CDN
- Multiple external BitTorrent peers (Redacted)

### Domains Observed

- beacons.gcp.gvt2.com
- ogads-pa.clients6.google.com
- rr6---sn-5fo-jomd.googlevideo.com

### Services

- Google Video CDN
- Google Beacons
- Cloudflare HTTPS
- BitTorrent P2P

### Malicious Indicators

**None Identified**

---

## 6. Detailed Analysis

The packet capture began with SSDP multicast discovery traffic followed by encrypted TLS communications and DNS lookups for legitimate Google services. The host resolved multiple Google-owned domains before establishing encrypted QUIC sessions over UDP port 443.

Several DNS queries resolved Google infrastructure including **beacons.gcp.gvt2.com**, **ogads-pa.clients6.google.com**, and **rr6---sn-5fo-jomd.googlevideo.com**, indicating legitimate browser and media-related activity.

Multiple UDP conversations were identified on port **6881**, a well-known BitTorrent port. The communication involved several external peers using both IPv4 and IPv6, demonstrating decentralized peer discovery and data exchange consistent with BitTorrent protocol behavior.

Additional multicast DNS (mDNS) traffic revealed Google Cast and Spotify service discovery requests, which are expected on local home networks containing smart devices.

Inspection of encrypted sessions showed normal TLS Application Data and QUIC Protected Payload traffic. Due to encryption, application contents could not be inspected; however, no suspicious connection patterns, beacon intervals, credential exposure, or indicators of compromise were identified.

---

## 7. Findings

The packet capture primarily consists of legitimate network communications.

Observed activity includes:

- Normal DNS resolution
- Encrypted HTTPS traffic
- QUIC communications with Google infrastructure
- Google Video content delivery
- SSDP and mDNS service discovery
- BitTorrent peer-to-peer networking

Although BitTorrent traffic is commonly monitored within enterprise environments due to policy concerns, the protocol itself is not malicious. No evidence of malware delivery, ransomware activity, phishing infrastructure, command-and-control communication, lateral movement, or data exfiltration was identified during analysis.

---

## 8. Recommendations

- Verify whether BitTorrent usage is authorized within the environment.
- Monitor or restrict UDP port 6881 if peer-to-peer applications violate organizational policy.
- Continue monitoring outbound encrypted traffic for abnormal behavioral patterns.
- Maintain updated endpoint protection and IDS/IPS signatures.
- Periodically review DNS requests for newly observed or suspicious domains.
- Educate users regarding risks associated with peer-to-peer file sharing.

---

## 9. Conclusion

The analyzed packet capture represents normal endpoint activity with legitimate encrypted communications, Google service interactions, local network discovery traffic, and BitTorrent peer-to-peer networking. No indicators of malware infection, command-and-control communication, phishing activity, credential theft, or data exfiltration were identified. While the observed peer-to-peer traffic increases potential exposure to malicious downloads, no evidence suggests the endpoint was compromised during the captured timeframe.

---

## 10. Analyst Skills Demonstrated

- Packet inspection using Wireshark
- Network protocol analysis
- DNS investigation
- TLS traffic analysis
- QUIC protocol analysis
- SSDP and mDNS analysis
- BitTorrent protocol identification
- Peer-to-peer traffic analysis
- IOC identification
- Network behavior analysis
- Risk assessment
- Security incident documentation
- Technical report writing
