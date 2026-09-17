# SOP: Monthly Headcount Report

| Field | Detail |
|---|---|
| **Process Owner** | Talent Processes and Business Support |
| **Frequency** | Monthly, 1st business day of the month |
| **System(s) Used** | Simulated HRIS export, Microsoft Excel |
| **Output** | `Headcount_Summary_[Month][Year].xlsx` distributed to Talent Business Advisory Team |

## Purpose
To produce a reliable, reconciled monthly headcount report by department and status, used for workforce planning and leadership reporting.

## Steps

1. **Pull the raw export**
   Extract the full employee roster from the HRIS as of the last calendar day of the month. Save as `employees_raw_[YYYYMM].csv`.

2. **Run the data audit checklist**
   Before reporting, check for:
   - Duplicate Employee IDs
   - Missing Department, Manager, or Name fields
   - Status/Termination Date contradictions (Active status with a Termination Date, or vice versa)
   - Inconsistent date formats
   Log every issue found in `Audit_Findings_[YYYYMM].md` using the standard template.

3. **Apply the data precedence rule**
   When two fields conflict, the **system-generated field takes precedence** over a manually entered one (e.g., Termination Date overrides a stale Active status).

4. **Flag, don't delete**
   Never delete a record with missing or conflicting data. Flag it clearly (e.g., "PENDING HR CONFIRMATION") so headcount totals aren't silently understated, and route it to the appropriate owner via the ticket queue.

5. **Build the report**
   Using the cleaned dataset, create an Excel summary showing:
   - Headcount by Department
   - Headcount by Status (Active / Terminated)
   - Month-over-month change

6. **Quality check before distribution**
   Confirm total headcount reconciles against last month's report +/- net hires/exits. Any variance greater than 5% must be investigated before distribution.

7. **Distribute**
   Share the finalized report with the Talent Business Advisory Team by end of day, 1st business day of the month.

## Escalation
If source data quality issues affect more than 5% of records, escalate to the HRIS systems team before publishing the report, rather than reporting on incomplete data.
