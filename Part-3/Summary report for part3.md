#  Integrity Audit of Water Quality Assessments – Maji Ndogo

This report documents the third phase of the Maji Ndogo water access audit, focused on validating field surveyor scores and investigating potential discrepancies or misconduct using the independent auditor’s report.

---

##  Objective

To validate water quality scores recorded by field surveyors by integrating the independent auditor’s report, and to investigate potential discrepancies or misconduct.

---

##  Methodology

### Data Integration
- Imported the auditor’s CSV report into the database as `auditor_report`.
- Joined with `visits`, `water_quality`, and `employee` tables to compare scores and link records to surveyors.

### Score Comparison
- Filtered for first-time visits only (`visit_count = 1`).
- Compared `true_water_source_score` (auditor) vs `subjective_quality_score` (surveyor).
- Created a view `Incorrect_records` to store all mismatched entries with employee names and auditor statements.

### Discrepancy Analysis
- Calculated number of mismatches per employee (`error_count`).
- Identified employees with above-average discrepancies (`suspect_list`).
- Cross-referenced auditor statements for qualitative evidence.

---

##  Key Findings

- **Score Agreement**: 1518 out of 1620 records matched — a 94% agreement rate.
- **Discrepancies**: 102 records showed mismatched scores.
- **Source Type Validation**: No discrepancies found in `type_of_water_source` — previous analyses remain valid.

### Suspect Employees
Four employees had above-average mistake counts:
- Zuriel Matembo
- Malachi Mavuso
- Bello Azibo
- Lalitha Kaburi

Auditor statements linked to these employees frequently mentioned “cash” and other concerning behavior.  
No other employees had similar allegations.

---

##  Implications

These findings suggest potential misconduct or bias in data collection by a small group of employees.  
While not conclusive proof of corruption, the combination of statistical anomalies and qualitative evidence warrants escalation.

---

##  Recommendations

- **Flag and Report**: Share findings with Pres. Naledi and relevant oversight bodies.
- **Investigate Further**: Conduct interviews and field reviews for the four flagged employees.
- **Training Review**: Reassess training and supervision protocols for field surveyors.
- **Audit Expansion**: Consider extending the audit to other regions or datasets.

---

##  Prepared by

**Rediet**  
Data Analyst & Economics Student  
Focused on ethical development, public accountability, and real-world impact through data
