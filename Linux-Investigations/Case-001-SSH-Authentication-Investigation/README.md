# Case-001 — Linux SSH Authentication Investigation

## Case Overview

| Field | Details |
|---|---|
| Case ID | LINUX-001 |
| Category | Linux Security / Authentication Analysis |
| Tool | Ubuntu 22.04.5 LTS |
| Analysis | Linux Authentication Logs |
| Log Source | /var/log/auth.log* |
| Endpoint | wazuh-server |
| Account | socadmin |
| Source IP | 100.112.15.4 |
| Disposition | Close — No Escalation |
| Status | Completed — Tier 1 assessment |

## Investigation Summary

Linux Secure Shell (SSH) authentication logs were analyzed to investigate two failed password attempts followed by a successful login.

The events occurred on November 12, 2026, from a Tailscale source address. The original records were recovered from rotated authentication logs using zgrep.

The account owner confirmed the login was authorized. The activity was classified as benign, with no evidence supporting unauthorized access.

## Key Findings

- Two failed SSH password attempts.
- One successful authentication 16 seconds after the first failure.
- Account: `socadmin`.
- Source IP: `100.112.15.4`.
- Source port: `55193`.
- Authentication occurred on November 12, 2026.
- A successful user session was established.
- Source address was consistent with Tailscale remote access.
- Account owner confirmed authorized activity.
- No brute-force attack or compromise was established.

## Evidence

- [SSH Authentication Sequence](evidence/01-ssh-authentication-sequence.png)
- [Authentication Log Investigation](evidence/02-authentication-log-investigation.png)

## Analyst Report

[Read the Full Analyst Report](analyst_report.md)

## Disposition

**Closed — Benign True Positive (authorized authentication activity).**

The authentication events were genuine, but the account owner confirmed the session was authorized.

No escalation or remediation was required based on the available evidence.

## Skills Demonstrated

- Linux authentication log analysis
- SSH security investigation
- Authentication event correlation
- Rotated log investigation
- Source IP analysis
- Benign activity identification
- Evidence-based classification
- SOC analyst reporting

## Investigation Limitations

The investigation relied on available authentication logs and account-owner confirmation.

No comprehensive endpoint activity review was performed. The investigation did not identify evidence supporting unauthorized access.

## Training Source

Independent Ubuntu Linux cybersecurity home lab.

