# Case-009 — Suspected C2 Beaconing and Data Exfiltration

**Investigation Type:** Network Forensics / DNS, TLS & HTTP Analysis  
**Environment:** Public malware-traffic training PCAP  
**Tools:** TShark, macOS Terminal  
**Classification:** Suspicious outbound traffic — Escalated  
**MITRE ATT&CK:** T1071.001 — Application Layer Protocol: Web Protocols (provisional)

## Investigation Summary

Investigated suspicious outbound network traffic from workstation `10.9.11.135` in a September 11, 2026 training PCAP.

Identified recurring DNS queries, approximately 48-second HTTPS communication intervals, and 18 HTTP POST requests to an external destination, including one declaring a 4,447,024-byte binary payload.

## Key Findings

- **Suspected Host:** `10.9.11.135`
- **HTTP Destination:** `know.mom-nower.com` (`86.106.87.134:80`)
- **Recurring TLS Hostnames:** `winrun2915.com`, `logincrypt8338.com`, `opscast3707.net`
- **Behavior:** Periodic HTTPS connections and repeated binary HTTP uploads
- **Response Analysis:** HTTP 200/204 responses; GZIP signature observed in one POST payload
- **Assessment:** Consistent with suspected C2 activity and possible data exfiltration
- **Limitation:** Malware execution and sensitive-data theft were not independently confirmed

## Evidence

![DNS Activity](evidence/01-dns-activity.png)

![TLS Beaconing](evidence/02-tls-beaconing.png)

![HTTP POST Activity](evidence/03-http-post-activity.png)

![HTTP Responses](evidence/04-http-responses.png)

![POST Pattern](evidence/05-post-pattern.png)

## Disposition

**Escalate to Tier 2 / Incident Response.**

Recommend preserving network evidence, investigating the initiating endpoint process, evaluating authorized containment, and determining the contents of transmitted data.

## Skills Demonstrated

TShark filtering · DNS analysis · TLS SNI correlation · HTTP payload analysis · Beaconing detection · Incident escalation

[Read the full investigation report](analyst_report.md)

**Training Source:** Malware-Traffic-Analysis.net — September 11, 2026 traffic analysis exercise.
