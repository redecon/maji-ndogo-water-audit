# 🌍 Maji Ndogo: From Analysis to Action

## 📘 Project Overview

This is a story-driven, SQL-powered data analysis project set in the fictional country of **Maji Ndogo**. The mission: help rejuvenate the drying **Mto wa Matumaini** — the River of Hope — using data to guide infrastructure upgrades, policy decisions, and ethical resource allocation.

The project simulates real-world challenges faced by development analysts, engineers, and public servants. It combines technical rigor with narrative immersion, guiding learners through a multi-phase journey from raw data to actionable insights.

---

## Project Structure

The project is divided into four parts, each building on the last:

### **Part 1: Starting the Journey**
- Explore a realistic water access database with over 60,000 records.
- Use SQL to clean, inspect, and understand foundational tables.
- Learn to write basic queries and uncover patterns in water source usage.

### **Part 2: Clustering the Crisis**
- Aggregate data to reveal the scale of Maji Ndogo’s water challenges.
- Use SQL functions and window functions to analyze queue times, contamination, and infrastructure reliability.
- Begin forming hypotheses and identifying priority areas.

### **Part 3: Weaving the Narrative**
- Join multiple tables to build a complete audit dataset.
- Investigate pollution types, broken infrastructure, and disparities between towns.
- Document findings and prepare for stakeholder reporting.

### **Part 4: Charting the Future**
- Finalize analysis and derive actionable goals.
- Create a `Project_progress` table to track engineering interventions.
- Use CASE logic to assign improvements based on contamination, queue times, and infrastructure status.
- Prepare a summary report for President Naledi and field teams.

---

##  Key Insights

- **43%** of citizens rely on shared taps, often queuing for over 120 minutes.
- **31%** have in-home infrastructure, but **45%** of those systems are broken.
- **18%** use wells, but only **28%** are clean.
- Towns like **Amina**, **Bahari**, and **Zuri** face severe infrastructure failures.
- Sokoto has the highest reliance on river water — a major health risk.

---

##  Technical Highlights

- SQL joins across `water_source`, `location`, `visits`, and `well_pollution`.
- Aggregation by province and town using composite keys.
- CASE logic to assign interventions:
  - Drill wells for river sources.
  - Install RO/UV filters for contaminated wells.
  - Add taps based on queue time thresholds.
  - Diagnose infrastructure for broken in-home taps.
- Creation of `Project_progress` table with status tracking and completion dates.

---

##  Project_progress Table

Tracks engineering tasks and upgrades:

```sql
CREATE TABLE Project_progress (
  project_id SERIAL PRIMARY KEY,
  town_name VARCHAR(100),
  province_name VARCHAR(100),
  source_type VARCHAR(50),
  action_required VARCHAR(255),
  status VARCHAR(50) DEFAULT 'Backlog' CHECK (status IN ('Backlog', 'In progress', 'Complete')),
  completion_date DATE,
  upgrade_notes TEXT
);
```
---

## Ethical Reflection
This project goes beyond technical analysis. It reveals systemic inequalities in water access, political bias in infrastructure allocation, and the human cost of broken systems. It challenges us to think critically, act ethically, and use data to serve communities with transparency and empathy.

---

## Learning Outcomes:
By completing this project, I:

- Mastered SQL for real-world data analysis.

- Learned to clean, join, and aggregate complex datasets.

- Translated insights into operational plans.

- Built stakeholder-ready reports and tracking systems.

- Understood the intersection of data, ethics, and public service.

---

## Credits

This project was developed by ALX and guided by Chidi Kunto — a fictional mentor and role model for ethical data leadership. All characters and places are fictional, but the challenges they represent are real.

Pula! (In Maji Ndogo, it means “rain” — a symbol of blessings and prosperity.)