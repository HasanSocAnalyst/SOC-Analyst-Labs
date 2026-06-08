# Case 002 - PowerShell ExecutionPolicy Bypass

## Scenario

A PowerShell process was launched using the ExecutionPolicy Bypass flag.

## Objective

Determine:

- What process was executed
- Which Sysmon event was generated
- Whether the activity appears malicious

## Tools Used

- Sysmon
- Event Viewer
- PowerShell

## Findings

- Event ID 1 detected
- PowerShell launched with:
  -ExecutionPolicy Bypass
  -NoProfile

## Classification

Benign Administrative Activity
