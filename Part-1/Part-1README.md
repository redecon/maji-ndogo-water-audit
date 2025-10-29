# Maji Ndogo Water Audit – Part 1

This part documents the first phase of a data integrity audit and water quality assessment for the town of **Maji Ndogo**. The analysis focuses on identifying misclassified water sources, contamination risks, and survey inconsistencies using SQL and real-world field data.

## 🔍 Objectives

- Explore foundational tables (`location`, `visits`, `water_sources`, `pollution_tests`)
- Identify anomalies in queue times and revisit patterns
- Audit subjective quality scores and contamination records
- Correct misclassified pollution data using SQL updates
- Verify data integrity through targeted queries

## 📊 Key Findings

- 218 records showed multiple visits to home taps (score = 10), violating survey protocol
- 4916 pollution records were misclassified due to misleading descriptions
- Biological contamination thresholds were misinterpreted, risking public health
- All errors were corrected and verified using reproducible SQL workflows

## 🛠️ Tools Used

- MySQL + PyMySQL
- Jupyter Notebook
- SQL (SELECT, UPDATE, LIKE, JOIN)
- Markdown for audit documentation

## ✅ Outcome

All misclassified records were corrected in a safe copy (`well_pollution_copy`) and verified using integrity checks. This sets the foundation for Part 2: regional analysis, visualization, and policy recommendations.


## 👩🏽‍💻 Author

**Rediet** – Economics + Data Analytics student  
Focused on global development, audit integrity, and technical storytelling  


---


