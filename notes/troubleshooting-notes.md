# Troubleshooting Notes

## Issue 1 — Event ID 107 Not Generated

### Cause

The Windows 11 build did not generate Task Scheduler Event ID 107 during maintenance execution.

### Resolution

Validate the remaining Task Scheduler Operational events instead of assuming a logging failure.

---

## Issue 2 — Missing Expected Task Scheduler Events

### Cause

Different Windows versions generate different Task Scheduler Operational events.

### Resolution

Enumerate recent Task Scheduler Operational logs using Event Viewer and PowerShell to determine which events are available.

---

## Issue 3 — No Results in Wazuh Discover

### Cause

Incorrect Event ID search or indexing delay.

### Resolution

Validate the events in Windows Event Viewer before troubleshooting Wazuh.

---

## Issue 4 — Event Viewer and PowerShell Differ

### Cause

PowerShell filtering or limited query range.

### Resolution

Use Event Viewer to identify available events and refine the PowerShell query.

---

## Issue 5 — Wazuh Agent Health

### Cause

Potential communication interruption.

### Resolution

Verify agent status:

```bash
sudo /var/ossec/bin/agent_control -i 001
```

---

# Lessons Learned

- Windows Task Scheduler Event IDs differ across Windows versions.
- Missing Event ID 107 does not indicate a logging problem.
- Event Viewer should always validate Windows event generation before investigating Wazuh.
- PowerShell and Event Viewer complement each other during DFIR investigations.
- Multiple evidence sources improve investigation reliability.
