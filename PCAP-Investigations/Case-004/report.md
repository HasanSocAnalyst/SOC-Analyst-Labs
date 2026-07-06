# SOC INCIDENT REPORT – NETWORK TRAFFIC ANALYSIS

## 1. Incident Overview

- **Incident ID:** CASE004
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

Analysis of the packet capture identified normal encrypted web traffic, peer-to-peer (P2P) communications, multicast service discovery, and internal network diagnostics. Multiple TLS 1.2 sessions were established with external HTTPS services, while UDP traffic over port 6881 indicated active BitTorrent peer discovery and communication with several IPv4 and IPv6 peers. Additional activity included mDNS service discovery for Google Cast devices and ICMP echo requests between the gateway and an internal host. No indicators of malware, command-and-control (C2) communications, phishing activity, or data exfiltration were identified during the investigation.

---

## 4. Network Traffic Summary

### Protocols Observed

- TCP
- UDP
- TLS 1.2
- ICMP
- mDNS

### Significant Ports

- TCP/443 (HTTPS)
- UDP/6881 (BitTorrent Peer-to-Peer)
- UDP/5353 (mDNS)

### Traffic Characteristics

- Encrypted HTTPS communications with multiple external servers
- Active BitTorrent peer discovery and peer communications
- IPv4 and IPv6 network traffic
- Local multicast DNS (mDNS) discovery for Google Cast devices
- ICMP echo requests and replies between the gateway and workstation
- No abnormal beaconing intervals observed
- No evidence of large outbound data transfers

---

## 5. Indicators Observed

### Internal Assets

- Internal Workstation: **Redacted**
- Default Gateway: **Redacted**

### External Infrastructure

- Cloudflare Infrastructure
- Multiple HTTPS servers
- GitHub Infrastructure
- Multiple external BitTorrent peers (Redacted)

### Services Observed

- HTTPS (TLS 1.2)
- BitTorrent Peer-to-Peer
- Google Cast Service Discovery
- mDNS
- ICMP Network Diagnostics

### Ports Observed

- TCP/443
- UDP/6881
- UDP/5353

### Malicious Indicators

**None Identified**

---

## 6. Detailed Analysis

The packet capture begins with several established HTTPS sessions over TCP port 443. The observed traffic consists primarily of TLS 1.2 Application Data exchanged between the internal workstation and multiple external web servers, indicating encrypted web browsing or application communications.

At approximately 2.48 seconds, the workstation begins communicating with numerous external IPv4 and IPv6 peers using UDP port 6881. This behavior is characteristic of BitTorrent peer discovery and decentralized peer-to-peer communication. Multiple inbound and outbound packets demonstrate active participation in a BitTorrent swarm rather than communication with a centralized command-and-control server.

Several encrypted TLS sessions continue throughout the capture while BitTorrent traffic remains active. The encrypted sessions appear consistent with legitimate HTTPS communications and do not exhibit periodic beaconing or repetitive callback intervals commonly associated with malware.

At approximately 6.08 seconds, multicast DNS (mDNS) queries are transmitted to locate Google Cast devices on the local network. These multicast discovery requests are expected within home or enterprise environments containing Chromecast-enabled devices.

The capture also contains ICMP echo requests and replies exchanged between the default gateway and the workstation, confirming successful network connectivity and normal diagnostic traffic.

No suspicious payloads, exploit attempts, credential exposure, malicious domains, or indicators of compromise were identified during packet inspection.

---

## 7. Findings

Analysis determined the network activity consists primarily of legitimate encrypted HTTPS communications combined with BitTorrent peer-to-peer networking.

Observed activity includes:

- Encrypted TLS 1.2 web traffic
- BitTorrent peer discovery
- Peer-to-peer communications over UDP port 6881
- Google Cast device discovery via mDNS
- Internal ICMP connectivity testing

Although BitTorrent traffic is commonly restricted within enterprise environments due to policy and security concerns, no evidence suggests malware delivery, ransomware activity, phishing, command-and-control communications, lateral movement, or data exfiltration within the analyzed capture.

---

## 8. Recommendations

- Review whether BitTorrent applications are authorized within the environment.
- Restrict or monitor UDP port 6881 if peer-to-peer traffic violates organizational policy.
- Continue monitoring encrypted outbound traffic for unusual behavioral changes.
- Maintain updated endpoint detection and response (EDR) and IDS/IPS signatures.
- Periodically review network traffic for abnormal peer communications.
- Educate users regarding the security risks associated with peer-to-peer file sharing.

---

## 9. Conclusion

The packet capture represents normal endpoint activity involving encrypted HTTPS communications, BitTorrent peer-to-peer networking, multicast DNS service discovery, and routine ICMP network diagnostics. No evidence of malware infection, command-and-control communication, phishing activity, credential theft, or data exfiltration was identified. While the observed BitTorrent activity increases the potential attack surface through external peer communications, the captured traffic does not indicate an active security incident.

---

## 10. Analyst Skills Demonstrated

- Packet inspection using Wireshark
- TCP and UDP traffic analysis
- TLS 1.2 traffic analysis
- BitTorrent protocol identification
- Peer-to-peer traffic analysis
- IPv4 and IPv6 traffic analysis
- mDNS service discovery analysis
- ICMP diagnostics analysis
- Network behavior analysis
- IOC identification
- Risk assessment
- Security incident documentation
- Technical report writing
