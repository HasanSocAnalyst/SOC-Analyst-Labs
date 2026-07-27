# Splunk Investigation Queries

Case ID: 004

Case Name: Registry Run Key Persistence 

Analyst: Hasan B

Date:

---

# Query 1

## Objective

Find Registry Run key modifications

### Search

```spl
index=main EventCode=13 TargetObject="*CurrentVersion\\Run*"
```

# Query 2

## Objective

Find the Registry value

### Search

```spl
index=main EventCode=13 Details="*notepad.exe*"
```
