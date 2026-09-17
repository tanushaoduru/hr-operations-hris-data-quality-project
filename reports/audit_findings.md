# Data Audit Findings — Monthly HRIS Export Reconciliation

**Prepared as:** HR Operations Portfolio Project
**Source file:** `data/raw/employees_raw.csv`
**Output file:** `data/processed/employees_cleaned.csv`
**Records in raw export:** 124
**Records after reconciliation:** 120
**Total data issues identified:** 23
**Resolved outright:** 7 (duplicates removed, status contradictions corrected)
**Flagged and routed for follow-up:** 16 (missing fields, missing termination dates)

## Summary of Issues Found and Resolution Applied

| Issue Type | Records Affected | Resolution Applied |
|---|---|---|
| Duplicate Employee ID | 4 | Kept the most complete record per ID per SOP; removed duplicate rows |
| Missing Employee Name | 2 | Flagged as "UNKNOWN - PENDING HR CONFIRMATION"; routed to source system owner for correction |
| Missing Department | 6 | Flagged as "UNASSIGNED - PENDING MANAGER INPUT"; escalated to reporting manager for update |
| Missing Manager | 5 | Flagged as "UNASSIGNED"; queued for HRBP follow-up |
| Status = Terminated but no Termination Date | 3 | Flagged for payroll/offboarding team confirmation before next report cycle |
| Status = Active but Termination Date present (contradiction) | 3 | Corrected Status to "Terminated" using Termination Date as source of truth, per data-precedence rule in SOP |
| Inconsistent date formats (raw file used 4 different formats) | 124 | Standardized all dates to ISO format (YYYY-MM-DD) during cleaning |

## Affected Employee IDs (for traceability)

- **Duplicates:** EMP1100, EMP1110, EMP1053, EMP1030
- **Missing name:** EMP1076, EMP1043
- **Missing department:** EMP1091, EMP1096, EMP1006, EMP1041, EMP1061, EMP1117
- **Missing manager:** EMP1050, EMP1085, EMP1102, EMP1104, EMP1049
- **Terminated, no date:** EMP1106, EMP1020, EMP1084
- **Status contradiction:** EMP1065, EMP1064, EMP1005

## Notes

- All corrections followed the precedence rule: **system-of-record field (Termination Date) overrides manually-entered Status field** when the two conflict.
- Records flagged as "PENDING" were **not deleted** — they were preserved with a clear flag so downstream reports don't silently drop headcount, and so the source-system owner has full traceability back to the original ticket.
- This reconciliation would normally be logged against a ticket ID in the shared services queue (see `/tickets/ticket_queue.csv` for the corresponding sample tickets).
