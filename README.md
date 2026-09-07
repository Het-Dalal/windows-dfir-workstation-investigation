# Windows DFIR Investigation
## Suspicious Workstation Activity — HD-DFIR-001

**Case Type:** Simulated Windows DFIR Investigation  
**Status:** Closed  
**Examiner:** Het Dalal  
**Tools:** Autopsy, Registry Explorer

---

## Case Overview

A Windows workstation was reviewed following suspicious after-hours activity associated with a user account.

The investigation focused on identifying the account involved, reconstructing the activity timeline, examining removable media, reviewing PowerShell activity and determining whether a sensitive financial file was transferred.

The investigation was performed without prior knowledge of the final incident outcome.

---

## Investigation Objectives

- Identify the account involved in the after-hours activity
- Establish the activity window
- Identify files accessed or transferred
- Examine suspicious executable activity
- Determine whether removable storage was involved
- Identify possible cleanup or anti-forensic activity
- Reconstruct the sequence of events

---

## Key Findings

The investigation identified after-hours activity associated with **Aarav Shah**.

During the relevant session:

- A SanDisk removable-storage device was connected
- `rclone.exe` activity was identified
- PowerShell activity involved `Q3_Financial_Forecast.xlsx`
- A `Copy-Item` command copied the file to the `E:\` volume
- File-hash activity involving the document was identified
- PowerShell history-clearing activity was observed
- `rclone.exe` was subsequently removed
- The removable device was disconnected shortly before the user session ended

---

## Timeline

| Time | Activity |
|------|----------|
| 18:31:06 | After-hours user activity begins |
| 18:33:12 | SanDisk removable device connected |
| 18:36:02 | rclone-related activity identified |
| 18:36:10 | Additional executable/user activity |
| During session | Financial Forecast file activity and transfer |
| During session | Cleanup-related activity identified |
| 19:10:08 | SanDisk removable device removed |
| 19:12:31 | User session ends |

---

## Investigator Working Timeline

![Handwritten investigation timeline](./notes/handwritten-timeline.jpg)

---

## Investigation Approach

The case was examined primarily using **Autopsy**, with **Registry Explorer** used where manual Registry examination was required.

Evidence was correlated across user activity, removable-media artifacts, PowerShell evidence, filesystem activity and timestamps.

---

## Case Files

- [Case Brief](./HD-DFIR-001_Case_Brief.pdf)
- [Full Forensic Investigation Report](./HD-DFIR-001_Forensic_Report.pdf)
- [Evidence Screenshots](./evidence/)
- [Investigator Notes](./notes/)

---

## Scope

This is a **simulated forensic investigation** created for DFIR practice and portfolio development.

The people, organization and incident scenario are fictional.

The investigation methodology, artifact analysis, evidence correlation and conclusions represent my own examination of the supplied evidence.
