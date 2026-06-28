# Investigation Report

## Room Information

Room Name: Linux Logging for SOC

Platform: TryHackMe

Category: Linux Security Monitoring

Completion Date: YYYY-MM-DD

---

## Objective

Understand how Linux logs are stored and how analysts can search them during investigations.

---

## Task Performed

### Task 1

Reviewed system logs stored in:

```bash
/var/log/syslog
```

---

### Task 2

Searched for contacted NTP servers.

Command used:

```bash
cat /var/log/syslog | grep Contacted
```

Result:

Multiple successful connections to NTP servers were identified.

---

### Task 3

Searched for Yama security module messages.

Command used:

```bash
cat /var/log/syslog | grep Yama
```

Result:

Kernel generated Yama security messages were located.

---

## Findings

### Finding 1

Observed successful NTP communications.

Evidence:

- Contacted NTP server entries present in syslog.

### Finding 2

Observed Yama kernel security messages.

Evidence:

- Kernel log entries referencing Yama.

---

## Commands Used

```bash
cat /var/log/syslog | grep Contacted

cat /var/log/syslog | grep Yama
```

---

## Lessons Learned

Linux logs provide valuable forensic evidence for:

- System activity
- Authentication attempts
- Service execution
- Network communications
- Security events

Understanding how to search logs quickly is an essential SOC analyst skill.

---

## Conclusion

Successfully analyzed Linux log sources and extracted relevant information using command-line filtering techniques.

The investigation demonstrated foundational Linux monitoring skills applicable to SOC environments.
