# SOC Investigation Report — Case-002

## 1. Incident Overview

- **Case ID:** PCAP-002
- **Investigation:** Suspected FormBook C2 Network Traffic
- **Capture Date:** August 9, 2026
- **Environment:** Public training PCAP — simulated enterprise network
- **Detection Source:** FormBook C2 alerts and PCAP analysis
- **Tools:** Wireshark, TShark
- **Disposition:** Escalation recommended

## 2. Executive Summary

Investigated suspicious outbound HTTP traffic originating from internal workstation `172.16.8.49`. Analysis identified repeated POST requests to three external destinations, with similar request formats, recurring communication intervals, and apparently encoded payloads.

The behavior is consistent with possible automated command-and-control activity. Although the exercise provided FormBook-related alerts, the packet evidence reviewed does not independently establish malware execution or successful data exfiltration.

## 3. Indicators of Interest

| Destination IP | HTTP Host | Request Path |
|---|---|---|
| 146.59.71.167 | www.grinswakebthu.info | /irpw/ |
| 38.182.168.246 | www.taibeinan.cc | /lqjm/ |
| 45.130.41.161 | www.legenda-sochi.com | /8nw8/ |

**Suspected Internal Host:** `172.16.8.49`

These indicators were observed in the historical training capture and should be evaluated in context before operational blocking.

## 4. Investigation Findings

**Host Identification:** HTTP traffic filtering identified `172.16.8.49` as the source of repeated outbound communications to the suspicious destinations.

**Communication Pattern:** The workstation generated multiple POST requests approximately 2–3 seconds apart within observed request sequences. Similar activity occurred sequentially across three external destinations.

**HTTP Characteristics:** The requests used `application/x-www-form-urlencoded` and contained apparently encoded or obfuscated data. One inspected POST to `www.grinswakebthu.info` reported a 2,305-byte request body.

**Response Analysis:** A `404 Not Found` response was observed during the investigation. This status does not independently establish that the overall communication was benign or unsuccessful.

**Evidence Limitations:** The contents and purpose of the transmitted data were not conclusively established. Endpoint execution, persistence, and confirmed data theft were outside the verified PCAP findings.

## 5. MITRE ATT&CK Mapping

**T1071.001 — Application Layer Protocol: Web Protocols**

Provisional mapping based on suspected C2 communications using HTTP requests.

## 6. Assessment and Escalation

**Classification:** Suspicious automated outbound communications consistent with possible C2 behavior.

**Recommended Escalation:** Tier 2 / Incident Response.

**Recommended Actions:**
- Preserve the PCAP and associated investigation evidence.
- Consider authorized network isolation of `172.16.8.49`.
- Evaluate blocking the identified suspicious external destinations.
- Correlate the activity with endpoint process and security telemetry.
- Determine whether sensitive data was transmitted or additional hosts were affected.

## 7. Conclusion

Network evidence supports escalation of workstation `172.16.8.49` for suspected C2-related activity. Repeated HTTP POST requests, similar payload structures, and sequential external communications provide a strong basis for further investigation.

Successful exfiltration and malware execution were not independently confirmed from the reviewed network evidence.

## 8. Evidence Reference

- `evidence/01-suspicious-http-requests.png`
- `evidence/02-c2-destination-comparison.png`
- `evidence/03-http-request-response.png`

**Source:** Malware-Traffic-Analysis.net, August 9, 2026 — *First to Last* training exercise.
