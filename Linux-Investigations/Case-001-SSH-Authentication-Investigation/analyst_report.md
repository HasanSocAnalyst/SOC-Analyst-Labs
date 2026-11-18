# Analyst Investigation Report — Case-001

## 1. Case Metadata

- **Case ID:** LINUX-001
- **Investigation Type:** Linux SSH Authentication Investigation
- **Primary Tool:** Ubuntu Linux Authentication Logs
- **Analysis Tool:** grep / zgrep
- **Endpoint:** wazuh-server
- **Operating System:** Ubuntu 22.04.5 LTS
- **Account:** socadmin
- **Source IP:** 100.112.15.4
- **Disposition:** Close — No Escalation
- **Assessment:** Benign True Positive — authorized authentication

## 2. Investigation Summary

Linux Secure Shell (SSH) authentication records were reviewed after identifying two failed password attempts followed by a successful login.

The activity involved account `socadmin` and source address `100.112.15.4` on November 12, 2026.

The original authentication sequence was recovered from rotated log files.

The account owner confirmed that the login was authorized Tailscale remote-access activity.

The investigation was closed as benign.

## 3. Key Findings

### 3.1 SSH Authentication Events

- November 12, 14:30:28 UTC — Failed password.
- November 12, 14:30:35 UTC — Failed password.
- November 12, 14:30:44 UTC — Accepted password.
- November 12, 14:30:44 UTC — User session opened.

### 3.2 Source Investigation

- Source IP: `100.112.15.4`.
- Source port: `55193`.
- Target account: `socadmin`.
- Authentication protocol: SSH.
- Source address was within the Tailscale address range.

### 3.3 Authentication Pattern

- Two failed attempts preceded successful authentication.
- All three attempts used the same source IP and port.
- The successful login occurred 16 seconds after the first failure.
- No sustained password-guessing pattern was established.

### 3.4 Log Investigation

The original events were recovered using zgrep to search current and rotated authentication logs.

The current authentication log did not contain the historical November 12 events.

The rotated logs preserved the failed attempts, successful authentication, and session establishment.

## 4. Analysis

The authentication sequence initially warranted investigation because unsuccessful password attempts were followed by a successful login.

However, two failures followed by success do not independently establish brute-force activity.

The source IP was consistent with the existing Tailscale remote-access environment.

The account owner confirmed that the authentication was authorized.

The available evidence therefore supports a benign authentication retry rather than unauthorized access.

## 5. Disposition

**Close — Benign True Positive.**

The authentication activity was genuine and authorized.

No evidence supporting brute-force activity, unauthorized access, or account compromise was identified.

No Tier 2 escalation was required.

## 6. Recommended Tier 2 Actions

No Tier 2 investigation was required after authorization was confirmed.

If similar activity occurs without authorization confirmation:

1. Verify the account owner and expected source device.
2. Review authentication frequency and targeted usernames.
3. Investigate successful sessions following repeated failures.
4. Review relevant account and privilege activity.
5. Escalate if unauthorized access indicators are identified.

## 7. Evidence and Limitations

Evidence is preserved in the accompanying `evidence/` directory.

The investigation used Linux authentication records, rotated log searches, and account-owner confirmation.

No comprehensive review of commands executed during the session was performed.

The evidence supports closure of the reviewed authentication event but does not constitute a complete endpoint security assessment.

## 8. Skills Demonstrated

- Linux SSH authentication investigation
- Authentication log filtering
- Rotated log recovery
- Failed and successful login correlation
- Source IP investigation
- Benign activity classification
- Evidence-based case closure
- SOC analyst reporting

