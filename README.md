# Windows DFIR Investigation
## Suspicious After-Hours Workstation Activity — HD-DFIR-001

**Case Type:** Simulated Windows DFIR Investigation  
**Examiner:** Het Dalal  
**Tools Used:** Autopsy, Registry Explorer  
**Status:** Investigation Complete

---

## Case Overview

This project documents a simulated Windows DFIR investigation involving suspicious after-hours activity on a workstation.

The investigation focused on reconstructing the user's activity, identifying the use of removable media, examining suspicious executable and PowerShell activity, and determining whether a sensitive financial document was transferred from the workstation.

The case was approached as a forensic investigation rather than a flag-based challenge, with findings based on correlation between multiple artifacts and timestamps.

---

## Investigation Objectives

The investigation aimed to determine:

- Which user account was active during the suspicious session?
- What occurred during the after-hours activity?
- Was removable storage connected to the workstation?
- Were suspicious tools or commands used?
- Was the financial document transferred?
- Was there evidence of cleanup or anti-forensic activity?
- What was the sequence of events?

---

## Key Findings

Analysis identified after-hours activity associated with the account of **Aarav Shah**.

The investigation established that:

- A SanDisk removable-storage device was connected during the session.
- `rclone.exe` activity occurred shortly after the session began.
- PowerShell activity involved `Q3_Financial_Forecast.xlsx`.
- A `Copy-Item` command copied the financial document from the user's Documents directory to the `E:\` volume.
- A file hash was calculated for the financial document.
- PowerShell history-clearing activity was identified.
- `rclone.exe` was subsequently deleted.
- The removable device was disconnected shortly before the session ended.

The sequence of artifacts is consistent with deliberate file-transfer activity followed by cleanup actions.

> **Forensic note:** The copy operation to `E:\` is directly supported by PowerShell evidence. Attribution of the `E:\` volume specifically to the connected SanDisk device depends on drive-letter/volume mapping evidence; without that mapping, the relationship should be treated as correlation.

---

## Investigation Timeline

| Time | Activity |
|------|----------|
| 18:31 | After-hours workstation activity begins |
| 18:33:12 | SanDisk removable device connected |
| 18:36:02 | `rclone.exe` activity identified |
| 18:36:10 | Additional rclone/user activity identified |
| During session | Financial document and PowerShell activity identified |
| During session | File transfer and cleanup-related activity identified |
| 19:10:08 | SanDisk removable device removed |
| ~19:12 | Investigated activity window ends |

---

## Tools Used

### Autopsy
Used for forensic artifact analysis, filesystem examination, deleted-file analysis, browser activity and timeline correlation.

### Registry Explorer
Used for examination and verification of relevant Windows Registry artifacts.

---

## Case Documentation

The repository contains two documents:

### Case Brief
The original investigation scenario and questions used to begin the examination.

**[View Case Brief](./HD-DFIR-002_Case_Brief.pdf)**

### Full Forensic Report
Complete investigation containing the methodology, evidence screenshots, artifact analysis, reconstructed timeline, findings and final assessment.

**[View Full Forensic Report](./HD-DFIR-002_Forensic_Report.pdf)**

---

## Repository Structure

```text
windows-dfir-workstation-investigation/
│
├── README.md
├── HD-DFIR-002_Case_Brief.pdf
└── HD-DFIR-002_Forensic_Report.pdf
