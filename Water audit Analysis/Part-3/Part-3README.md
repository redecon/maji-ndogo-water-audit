# Maji Ndogo Water Access Audit – Part 3: Weaving the Data Threads

This phase focused on integrating the auditor’s independent report with our existing water access database to validate surveyor scores, uncover discrepancies, and investigate potential integrity issues among field employees.

---

## Contents

- `auditor_report.csv`: Independent audit results
- `Incorrect_records` : Mismatched scores with employee and statement data
- `error_count` (CTE): Mistake count per employee
- `suspect_list` (CTE): Employees with above-average discrepancies
- `suspect_statements.`: Qualitative evidence linked to suspect employees

---

##  Key Objectives

1. Integrate auditor data with SQL database
2. Compare auditor vs surveyor water quality scores
3. Validate source type consistency
4. Identify employees with above-average discrepancies
5. Cross-reference with auditor statements for potential misconduct

---

##  Audit Integration Workflow

###  Step 1: Load Auditor Report
- Created `auditor_report` table using schema
- Imported CSV via Pandas and SQLAlchemy

###  Step 2: Compare Scores
- Joined `auditor_report`, `visits`, and `water_quality`
- Filtered for first-time visits (`visit_count = 1`)
- Found 1518 matches out of 1620 (94% agreement)

###  Step 3: Validate Source Types
- Compared `type_of_water_source` from `auditor_report` and `water_source`
- Found full agreement — previous analyses remain valid

---

##  Integrity Analysis

### Step 4: Create `Incorrect_records` View
- Captures mismatched scores, employee names, and auditor statements

###  Step 5: Count Mistakes per Employee
```sql
WITH error_count AS (
  SELECT employee_name, COUNT(*) AS number_of_mistakes
  FROM Incorrect_records
  GROUP BY employee_name
)
```
### Step 6: Identify Suspects
```sql
WITH suspect_list AS (
  SELECT employee_name, number_of_mistakes
  FROM error_count
  WHERE number_of_mistakes > (SELECT AVG(number_of_mistakes) FROM error_count)
)
```
### Step 7: Cross-Reference Statements
```sql
SELECT employee_name, location_id, statements
FROM Incorrect_records
WHERE employee_name IN (SELECT employee_name FROM suspect_list)
  AND statements LIKE '%cash%';

```
##  Acknowledgments

This work is led by myself **Rediet**, a third-year Economics student and data analyst committed to solving real-world development challenges with strategic thinking, SQL mastery, and stakeholder empathy shaped this impactful analysis.