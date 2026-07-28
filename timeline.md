# Investigation Timeline

| Time | Activity | Evidence |
|------|----------|----------|
| 09:00 | Verified Wazuh agent connectivity | agent_control |
| 09:05 | Executed Windows maintenance task | Task Scheduler |
| 09:10 | Reviewed Task Scheduler Operational log | Event Viewer |
| 09:15 | Validated maintenance events | PowerShell |
| 09:18 | Observed Event IDs 100, 102, and 129 | Event Viewer |
| 09:22 | Confirmed Event ID 107 was not generated | Event Analysis |
| 09:28 | Investigated Wazuh Discover | Discover |
| 09:35 | Correlated findings | Documentation |

---

# Investigation Flow

Investigation Started

↓

Verified Agent Health

↓

Executed Windows Maintenance Task

↓

Reviewed Event Viewer

↓

Validated Using PowerShell

↓

Troubleshot Missing Event ID 107

↓

Investigated Wazuh Discover

↓

Correlated Evidence

↓

Investigation Completed

---

# Summary

The investigation reconstructed Windows maintenance activity using native Task Scheduler Operational logs and Wazuh Discover. The lab demonstrated successful validation of Event IDs **100**, **102**, and **129**, while showing that Event ID **107** was not generated on the test system. The investigation emphasized validating Windows logging, correlating multiple evidence sources, and documenting realistic DFIR findings.
