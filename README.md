# wazuh-windows-maintenance-activity-investigation-dfir-lab
## Overview

This Digital Forensics and Incident Response (DFIR) lab demonstrates how Windows maintenance activity can be investigated using native Windows Task Scheduler Operational logs and Wazuh.

Unlike Sysmon-based investigations, this lab relies entirely on Windows Event Logs, Event Viewer, PowerShell, Task Scheduler, and Wazuh Discover to reconstruct maintenance task execution.

The investigation also includes troubleshooting scenarios where expected Task Scheduler Event IDs are not generated, demonstrating how analysts validate Windows logging before drawing conclusions.

---

# Executive Summary

This investigation focused on analyzing Windows maintenance activity using native Windows Task Scheduler logs and Wazuh.

The investigation included:

- Executing a Windows maintenance task
- Investigating Task Scheduler Operational Event IDs
- Validating events using Event Viewer
- Verifying events using PowerShell
- Searching maintenance events in Wazuh Discover
- Troubleshooting missing Event ID 107
- Correlating Windows evidence with Wazuh

The investigation emphasizes structured DFIR methodology by validating Windows logs before relying solely on SIEM results.

---

# Learning Objectives

- Understand Windows maintenance tasks.
- Investigate Task Scheduler Operational logs.
- Validate maintenance events using Event Viewer.
- Verify events using PowerShell.
- Investigate maintenance activity using Wazuh Discover.
- Troubleshoot missing Task Scheduler events.
- Reconstruct a maintenance activity timeline.

---

# Skills Demonstrated

- Windows DFIR Investigation
- Windows Task Scheduler Analysis
- Windows Event Log Analysis
- Event Viewer Analysis
- PowerShell Event Validation
- Wazuh Discover Investigation
- Windows Event Correlation
- Timeline Reconstruction
- Digital Evidence Documentation
- DFIR Troubleshooting
- MITRE ATT&CK Mapping

---

# Tools Used

- Wazuh Dashboard (Discover)
- Windows Event Viewer
- Windows PowerShell
- Task Scheduler
- Windows Task Scheduler Operational Log
- Wazuh Agent

---

# Lab Environment

| Component | Details |
|-----------|---------|
| SIEM | Wazuh 4.12 |
| Endpoint | Windows 11 Pro |
| Server | Oracle Linux 9 |
| Investigation Type | Windows DFIR |
| Event Source | Task Scheduler Operational Log |
| Sysmon | Not Used |

---

# Investigation Scenario

A Windows maintenance task was manually executed through Task Scheduler.

As the DFIR analyst, the objectives were to determine:

- When the maintenance task executed
- Which Task Scheduler events were generated
- Whether Wazuh collected the activity
- Why Event ID 107 was not generated
- Whether the observed activity represented normal Windows maintenance

---

# Investigation Workflow

1. Verify Wazuh agent connectivity.
2. Execute a Windows maintenance task.
3. Review Task Scheduler Operational logs.
4. Validate events using Event Viewer.
5. Verify events using PowerShell.
6. Investigate activity using Wazuh Discover.
7. Troubleshoot missing Event ID 107.
8. Correlate investigative findings.
9. Document evidence.

---

# MITRE ATT&CK Mapping

| Tactic | Technique | ID |
|---------|-----------|----|
| Persistence | Scheduled Task/Job | T1053.005 |
| Defense Evasion | Scheduled Task | T1053.005 |

### Why Maintenance Investigations Matter

Windows maintenance tasks execute regularly on enterprise endpoints. Attackers frequently abuse scheduled tasks to blend malicious execution with legitimate administrative activity. Investigating Task Scheduler Operational logs helps analysts distinguish normal maintenance from suspicious persistence mechanisms.

---

# Evidence Collected

- Task Scheduler
- Windows Task Scheduler Operational Log
- Event Viewer
- PowerShell validation
- Wazuh Discover searches

---

# Evidence Correlation

| Evidence Source | Information Obtained | Investigation Value |
|-----------------|---------------------|--------------------|
| Task Scheduler | Task execution | Activity performed |
| Event Viewer | Task Scheduler events | Primary evidence |
| PowerShell | Event validation | Independent verification |
| Wazuh Discover | Collected events | SIEM validation |

---

# Investigation Findings

- A Windows maintenance task executed successfully.
- Windows generated Task Scheduler Event IDs 100, 102, and 129.
- Event ID 107 was not generated on the test system.
- Event generation was validated using Event Viewer and PowerShell.
- Wazuh successfully collected the maintenance activity.
- The investigation demonstrated successful correlation between Windows Task Scheduler logs and Wazuh Discover.

---

# Key Takeaways

- Task Scheduler Operational logs are valuable DFIR evidence.
- Windows versions may generate different Task Scheduler Event IDs.
- Event Viewer and PowerShell should always be used to validate Windows logging.
- Missing Event IDs do not necessarily indicate SIEM collection issues.
- Wazuh Discover provides centralized visibility into Windows maintenance activity.

---
