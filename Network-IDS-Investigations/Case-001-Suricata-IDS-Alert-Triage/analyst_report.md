# Analyst Investigation Report — Case-001

## 1. Case Metadata
- **Case ID:** Network-IDS-001
- **Investigation Type:** Network IDS Alert Triage
- **Primary Tool:** Suricata 6.0.4
- **Analysis Tool:** tshark
- **PCAP:** `2026-02-28-traffic-analysis-exercise.pcap`
- **Internal Host:** `10.2.28.88`
- **External Destination:** `45.131.214.85`
- **Disposition:** Escalate to Tier 2
- **Assessment:** Suspicious — suspected malicious remote-access activity

## 2. Investigation Summary
An offline packet capture was processed by Suricata to identify network activity matching its detection rules. The analysis generated repeated NetSupport Remote Admin Checkin and Response alerts involving internal host `10.2.28.88` and external destination `45.131.214.85`.

Further inspection with tshark identified recurring HTTP POST requests using the `NetSupport Manager/1.3` user-agent and the URI `/fakeurl.htm`. Request bodies contained `CMD=POLL` and `CMD=ENCD` fields, with encoded-looking data.

The traffic pattern and application indicators warranted escalation for validation of the software, endpoint, and external destination.

## 3. Key Findings

### 3.1 Suricata Alerts
- 264 `ET INFO NetSupport Remote Admin Checkin` alerts.
- 2 `ET INFO NetSupport Remote Admin Response` alerts.
- 264 `ET POLICY HTTP traffic on port 443 (POST)` alerts.

### 3.2 Network Communication
- Source: `10.2.28.88`
- Destination: `45.131.214.85`
- Protocol: TCP
- Destination port: 443
- Repeated outbound communication occurred at approximately 60-second intervals.

### 3.3 HTTP Indicators
- Method: POST
- User-agent: `NetSupport Manager/1.3`
- URI: `/fakeurl.htm`
- Request body fields included `CMD=POLL`, `INFO=1`, `ACK=1`, and repeated `CMD=ENCD` messages.
- The `DATA` field contained encoded-looking content that was not decoded during this investigation.

### 3.4 DNS Investigation
A DNS filter for traffic involving `45.131.214.85` returned no matching packets. This means no matching DNS activity was observed in the supplied capture. It does not establish whether the destination was resolved previously or through another mechanism.

## 4. Analysis
The recurring communication pattern is consistent with periodic check-in behavior. The NetSupport user-agent and application fields indicate NetSupport-related network communication.

NetSupport is legitimate remote-management software, but it can also be abused. The repeated communication, unusual request URI, and encoded-looking request data collectively justify further investigation.

The available packet evidence does not establish whether the software was authorized, whether remote commands were executed, or whether sensitive information was transferred.

## 5. Disposition
**Escalate to Tier 2 for further investigation.**

The activity is classified as suspicious and potentially malicious. The available evidence supports escalation but is insufficient to confirm endpoint compromise or data exfiltration.

## 6. Recommended Tier 2 Actions
1. Identify the process responsible for the network connection on `10.2.28.88`.
2. Determine whether NetSupport Manager was installed and authorized.
3. Review endpoint telemetry for remote-access activity, process execution, and persistence.
4. Investigate the reputation, ownership, and business purpose of `45.131.214.85`.
5. Determine whether the encoded application data contains commands or transferred information.
6. Correlate the network activity with endpoint and SIEM logs.

## 7. Evidence and Limitations
Evidence is preserved in the accompanying `evidence/` directory.

This investigation was limited to the supplied packet capture. No endpoint telemetry, software inventory, authorization records, destination attribution, or decoded application payload was available.

## 8. Skills Demonstrated
- Network IDS alert triage
- Suricata offline PCAP processing
- tshark packet filtering
- TCP traffic analysis
- HTTP request and payload inspection
- Periodic communication analysis
- Evidence-based escalation
- SOC analyst reporting
