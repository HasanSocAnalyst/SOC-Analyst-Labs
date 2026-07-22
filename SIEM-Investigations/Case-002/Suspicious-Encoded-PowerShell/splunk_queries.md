# Splunk Queries — SIEM-002

---

## Query 1 — Verify PowerShell telemetry

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational"
```

### Purpose

Confirm PowerShell Operational logs are arriving.

---

## Query 2 — Find Script Block events

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" EventID=4104
```

### Purpose

Locate PowerShell script execution.

---

## Query 3 — Detect encoded commands

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 "-EncodedCommand"
```

### Purpose

Identify encoded PowerShell execution.

---

## Query 4 — Extract execution context

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-Sysmon/Operational" EventID=1 "-EncodedCommand"
| table _time Computer User ParentImage Image CommandLine ProcessGuid
```

### Purpose

Identify user, parent process, and command line.

---

## Query 5 — Verify decoded command

### Search

```spl
index=main source="XmlWinEventLog:Microsoft-Windows-PowerShell/Operational" EventID=4104 "Get-ComputerInfo"
```

### Purpose

Confirm the decoded PowerShell command.

