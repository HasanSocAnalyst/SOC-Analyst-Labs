# WAZUH-002 — Suspicious PowerShell Execution

## Overview

This investigation analyzes a PowerShell execution detected by Wazuh on a monitored Windows 10 endpoint. The objective was to verify endpoint telemetry, investigate the generated alert, review the associated Wazuh detection rule, and determine whether the activity represented legitimate administrative activity or malicious behavior.

## Objective

Investigate a PowerShell execution detected by Wazuh to determine:

- The originating process
- The affected endpoint
- The executing user
- The Wazuh detection rule
- The associated MITRE ATT&CK technique
- Whether the activity is benign or suspicious

## Environment

- Windows 10 22H2
- Wazuh Server 4.14.7
- Wazuh Agent 4.14.7
- PowerShell 5.1

## Telemetry Generated

The following PowerShell commands were executed to generate endpoint telemetry:

```powershell
Get-ComputerInfo
Get-Service
Get-Process
