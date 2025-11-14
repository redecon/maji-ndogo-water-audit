# Maji Ndogo Water Access Audit – Summary Report

## Project Overview

This project analyzes water access data in Maji Ndogo to identify infrastructure gaps, contamination risks, and service inefficiencies. Using SQL and structured joins across multiple tables, we built a unified dataset and translated insights into a prioritized action plan. The final output includes a `Project_progress` table to help engineering teams track repairs and upgrades.

---

## What I Did

###  Data Integration
- Joined `location`, `visits`, `water_source`, and `well_pollution` tables using `source_id` and `location_id`.
- Filtered for first-time visits (`visit_count = 1`) to avoid duplicate records.
- Created a unified view (`combined_analysis_table`) with:
  - Geographic context (province, town, location type)
  - Source type and population served
  - Queue times and pollution results

### Pivot Table Analysis
- Aggregated water source usage by **province** and **town**.
- Calculated percentage of population served by:
  - Rivers
  - Shared taps
  - In-home taps (working and broken)
  - Wells (clean and contaminated)
- Identified disparities in access and infrastructure reliability.

###  Key Insights
- 43% of people rely on shared taps; queues often exceed 120 minutes.
- 31% have in-home infrastructure, but 45% of those systems are broken.
- 18% use wells, but only 28% are clean.
- Sokoto has the highest reliance on river water.
- Amina has widespread broken infrastructure despite high tap installation rates.

---

##  Action Plan

### Priorities
1. **Shared taps**: Install additional taps where queues exceed 30 minutes.
2. **Wells**: Install RO and UV filters based on contamination type.
3. **Broken taps**: Diagnose and repair infrastructure in towns like Amina, Lusaka, Zuri, and Djenne.
4. **River water**: Drill wells in Sokoto and dispatch water trucks short-term.

### Engineering Strategy
- Focus on rural areas with poor road access and limited labor.
- Use queue time data to optimize tanker dispatch schedules.
- Target high-impact repairs (e.g., reservoirs, pumps) that benefit thousands.

---

##  Project Tracking Table

We created a `Project_progress` table to track engineering tasks:

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
