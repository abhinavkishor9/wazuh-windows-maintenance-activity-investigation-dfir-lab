# Investigation Notes

## Lab Summary

This investigation focused on analyzing Windows maintenance activity using native Task Scheduler Operational logs and Wazuh Discover.

The investigation reconstructed maintenance execution by correlating Task Scheduler, Event Viewer, PowerShell, and Wazuh while validating maintenance-related events.

---

## Analyst Methodology

1. Verify Wazuh agent connectivity.
2. Execute a Windows maintenance task.
3. Review Task Scheduler Operational logs.
4. Validate events using Event Viewer.
5. Verify events using PowerShell.
6. Search Wazuh Discover.
7. Troubleshoot missing Event ID 107.
8. Correlate evidence.
9. Document findings.

---

## Investigation Scenario

A Windows maintenance task was executed manually.

The investigation aimed to determine:

- Which maintenance events were generated.
- Whether Wazuh collected the activity.
- Why Event ID 107 was absent.
- Whether the activity represented legitimate Windows maintenance.

---

## Evidence Collected

### Evidence 1 – Task Scheduler

Collected:

- Manual maintenance task execution

Finding:

Established investigation baseline.

---

### Evidence 2 – Event Viewer

Collected:

- Task Scheduler Operational Log
- Event IDs 100, 102, 129

Finding:

Confirmed successful maintenance task execution.

---

### Evidence 3 – PowerShell Validation

Command Used

```powershell
Get-WinEvent -LogName "Microsoft-Windows-TaskScheduler/Operational" -MaxEvents 30
```

Finding:

Confirmed Event IDs 100, 102, and 129. Event ID 107 was not generated.

---

### Evidence 4 – Wazuh Discover

Collected:

- Task Scheduler Operational events

Finding:

Validated successful collection of maintenance activity.

---

## DFIR Analysis

The investigation demonstrated that Windows maintenance tasks can be reconstructed using native Task Scheduler Operational logs.

Although Event ID 107 was not generated, Windows successfully produced sufficient evidence to reconstruct the maintenance activity and validate collection by Wazuh.

---

## MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Persistence | Scheduled Task/Job | T1053.005 |
| Defense Evasion | Scheduled Task | T1053.005 |

---

## Analyst Observations

- Event IDs vary across Windows builds.
- Event Viewer remains the authoritative evidence source.
- PowerShell provides rapid validation.
- Wazuh successfully collected Task Scheduler events.
- Multiple evidence sources improve investigation confidence.

---

## Conclusion

The investigation demonstrated how Windows maintenance activity can be reconstructed using Task Scheduler Operational logs and Wazuh Discover while emphasizing structured validation and troubleshooting when expected Task Scheduler events are not generated.
