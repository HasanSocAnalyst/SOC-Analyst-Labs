# SOC Investigation Report — Case-009

## 1. Incident Overview

- **Case ID:** PCAP-009
- **Investigation:** Suspected C2 Beaconing and Data Exfiltration
- **Capture Date:** September 11–12, 2026
- **Environment:** Public training PCAP — simulated enterprise network
- **Detection Source:** Network traffic analysis
- **Tools:** TShark, macOS Terminal
- **Disposition:** Escalation recommended

## 2. Executive Summary

Investigated suspicious outbound traffic from workstation `10.9.11.135`. Analysis identified recurring DNS requests, periodic HTTPS communications, and 18 HTTP POST requests to `know.mom-nower.com`.

One POST declared a 4,447,024-byte binary payload, followed by an HTTP 204 response. The combined activity supports suspected C2 communication and possible data exfiltration, but malware execution and sensitive-data theft remain unconfirmed.

## 3. Indicators of Interest

| Destination | Protocol | Observed Behavior |
|---|---|---|
| `know.mom-nower.com` / `86.106.87.134` | HTTP/80 | Repeated GET/POST requests |
| `winrun2915.com` | HTTPS/443 | Recurring TLS connections |
| `logincrypt8338.com` | HTTPS/443 | Recurring TLS connections |
| `opscast3707.net` | HTTPS/443 | Recurring TLS connections |
| `globalcert8618.net`, `opsbox8097.com`, `hostjob3862.net` | DNS | Repeated NXDOMAIN responses |

**Suspected Internal Host:** `10.9.11.135`

Indicators originate from a historical training capture and require contextual validation before operational blocking.

## 4. Investigation Findings

**DNS Activity:** Repeated queries to three similarly structured domains returned NXDOMAIN responses at approximately 48-second intervals.

**HTTPS Beaconing:** Three TLS hostnames appeared in a recurring sequence, approximately 16 seconds apart, with each hostname repeating around every 48 seconds. Associated TCP/443 endpoints returned SYN-ACK responses.

**HTTP Uploads:** Identified 18 POST requests to `know.mom-nower.com`, all reporting `application/octet-stream`. The largest declared request body was 4,447,024 bytes at 03:10:03 (UTC+7). One inspected payload began with the GZIP signature `1f8b08`.

**Response Analysis:** The server returned HTTP 200 and 204 responses. A 204 response occurred approximately four seconds after the largest POST.

**Additional Pattern:** Later traffic repeatedly paired 75-byte POST requests with approximately 26.6 KB POST requests.

**Evidence Limitations:** The complete payload contents, responsible endpoint process, and presence of sensitive information were not established. HTTP success responses do not independently prove data theft.

## 5. MITRE ATT&CK Mapping

**T1071.001 — Application Layer Protocol: Web Protocols**

Provisional mapping based on suspected C2 communications over HTTP/HTTPS.

**T1041 — Exfiltration Over C2 Channel**

Possible technique; insufficient evidence to confirm exfiltration.

## 6. Assessment and Escalation

**Classification:** Suspicious automated outbound communications consistent with possible C2 activity and data exfiltration.

**Priority:** High  
**Recommended Escalation:** Tier 2 / Incident Response

**Recommended Actions:**
- Preserve the PCAP and investigation evidence.
- Correlate network activity with endpoint process and EDR telemetry.
- Investigate the suspicious domains and related infrastructure.
- Consider authorized endpoint containment.
- Determine whether sensitive data was transmitted.

## 7. Conclusion

Recurring HTTPS communication, unusual DNS activity, and repeated binary HTTP uploads provide strong grounds for escalation of workstation `10.9.11.135`.

The investigation identified possible C2 and exfiltration behavior. Confirmed malware execution and sensitive-data theft were not established from the reviewed evidence.

## 8. Evidence Reference

- `evidence/01-dns-activity.png`
- `evidence/02-tls-beaconing.png`
- `evidence/03-http-post-activity.png`
- `evidence/04-http-responses.png`
- `evidence/05-post-pattern.png`

**Source:** Malware-Traffic-Analysis.net — September 11, 2026 traffic analysis exercise.
