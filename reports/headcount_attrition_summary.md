# Headcount & Attrition Summary — Sample Reporting Cycle

**Source:** `data/processed/employees_cleaned.csv` (post-reconciliation)
**Total headcount (all statuses):** 120
**Active employees:** 103
**Terminated employees:** 17
**Attrition rate:** 14.2%

## Headcount by Department

| Department | Headcount |
|---|---|
| Total Rewards | 22 |
| HR Operations | 17 |
| HRIS & Systems | 16 |
| Mobility | 14 |
| Talent Development | 14 |
| Talent Acquisition | 12 |
| Payroll | 10 |
| Talent Business Advisory | 9 |
| UNASSIGNED - PENDING MANAGER INPUT | 6 |

## Performance Rating Distribution

| Rating | Count |
|---|---|
| Meets Expectations | 48 |
| Needs Improvement | 25 |
| Exceeds Expectations | 24 |
| Not Yet Rated | 23 |

## Notes for Stakeholders
- This report reflects the **reconciled** dataset. 23 data-quality findings were identified during the audit; 7 were resolved and 16 were flagged for follow-up (see `audit_findings.md` for the full log).
- Records with unresolved department information are retained under an UNASSIGNED category so that total headcount remains fully reconciled and no employees are silently excluded from reporting.
- This is a sample ad hoc report matching ticket TCK-1004 in the ticket queue.
