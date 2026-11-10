# Case-001 — Suricata IDS Alert Triage

## Case Overview
| Field | Details |
|---|---|
| Case ID | Network-IDS-001 |
| Category | Network IDS / Network Forensics |
| Tool | Suricata 6.0.4 |
| Analysis | tshark |
| Capture | 2026-02-28-traffic-analysis-exercise.pcap |
| Internal Host | 10.2.28.88 |
| External Destination | 45.131.214.85 |
| Disposition | Escalate to Tier 2 |
| Status | Completed — Tier 1 assessment |

## Investigation Summary
An offline PCAP was analyzed using Suricata and tshark. Suricata identified repeated NetSupport remote-access-related alerts involving an internal host communicating with an external destination.

Packet-level analysis identified recurring HTTP POST requests, a NetSupport Manager user-agent, the `/fakeurl.htm` URI, and request bodies containing `CMD=POLL` and `CMD=ENCD` fields.

The communication pattern and application indicators were considered suspicious and recommended for Tier 2 investigation.

## Key Findings
- Suricata processed 15,512 packets.
- 264 NetSupport Remote Admin Checkin alerts.
- 2 NetSupport Remote Admin Response alerts.
- 264 HTTP POST policy alerts.
- Repeated communication approximately every 60 seconds.
- HTTP user-agent: `NetSupport Manager/1.3`.
- Observed URI: `/fakeurl.htm`.
- HTTP POST bodies included `CMD=POLL` and `CMD=ENCD`.
- No matching DNS query was found in the supplied capture.

## Evidence
- [Suricata PCAP Processing](evidence/01-suricata-pcap-processing.png)
- [Suricata Alert Summary](evidence/02-suricata-alert-summary.png)
- [NetSupport Alerts](evidence/03-netsupport-alerts.png)
- [TCP Connection Analysis](evidence/04-tcp-connection-analysis.png)
- [Periodic Traffic Analysis](evidence/05-periodic-traffic-analysis.png)
- [HTTP Request Analysis](evidence/06-http-request-analysis.png)
- [HTTP Payload Analysis](evidence/07-http-payload-analysis.png)
- [Suricata Fast Log](evidence/suricata-fast.log)
- [Suricata Statistics](evidence/suricata-stats.log)
- [Investigation Command Output](evidence/investigation-command-output.txt)

## Analyst Report
[Read the Full Analyst Report](analyst_report.md)

## Disposition
**Escalate to Tier 2 — suspected malicious NetSupport remote-access activity.**

The PCAP supports a suspicious activity assessment but does not independently prove endpoint compromise, unauthorized use, command execution, or data exfiltration.

## Skills Demonstrated
- Suricata IDS alert triage
- Offline PCAP analysis
- tshark filtering and packet inspection
- TCP connection analysis
- HTTP request and payload analysis
- Identification of periodic network communication
- Suspicious remote-access activity assessment
- Evidence documentation and escalation

## Investigation Limitations
This investigation was limited to the supplied PCAP. Endpoint process telemetry, software authorization records, destination attribution, and decoded application data were not available.

## Training Source
Network traffic analysis exercise supplied for this investigation.
