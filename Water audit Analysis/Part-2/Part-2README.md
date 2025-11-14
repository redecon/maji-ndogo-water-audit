#  Maji Ndogo Water Access Analysis – Part Two

This phase of the project focused on analyzing water source distribution, infrastructure quality, and queue times across Maji Ndogo. Using SQL and strategic reasoning, we uncovered patterns that inform repair priorities and policy decisions.

---

##  Contents

- `location_analysis`: Town-level and type-level source distribution
- `water_source_summary`: Total and average population served per source
- `queue_time_analysis`: Queue duration breakdown by hour and day
- `pivot_queue_table`: Hourly queue time pivot table across weekdays
- `repair_prioritization`: Ranking sources by population served
- `summary_report.ipynb`: Executive summary

---

##  Key Insights

1. **Source Distribution**
   - Most water sources are located in rural areas.
   - Shared taps are the most common and most strained source.

2. **Population Served**
   - 43% of citizens rely on shared taps (~2000 people per tap).
   - 31% have taps at home, but 45% of those systems are broken.
   - 18% use wells, but only 28% are clean.

3. **Queue Time Analysis**
   - Average queue time exceeds 50 minutes.
   - Longest queues occur on Saturdays and weekday mornings/evenings.
   - Sundays and Wednesdays have the shortest queues.

4. **Pivot Table (Queue Time by Hour & Day)**
   - Built using `CASE()` and `AVG()` to simulate a pivot table in SQL.
   - Revealed cultural and behavioral patterns in water collection.

5. **Repair Prioritization**
   - Ranked source types and individual sources using `RANK()` and `ROW_NUMBER()`.
   - Focused on shared taps, wells, and broken infrastructure.
   - Excluded optimal sources like functional home taps from priority list.

---

##  Strategic Plan Highlights

- **Short-Term Actions**
  - Dispatch water trucks to river-dependent communities.
  - Install filters on contaminated wells.
  - Send tankers to high-queue shared taps during peak hours.

- **Medium-Term Actions**
  - Repair broken infrastructure (pipes, reservoirs) to restore home access.
  - Install additional shared taps to reduce load.

- **Long-Term Vision**
  - Investigate contamination sources.
  - Consider home tap installations where feasible.
  - Aim to reduce queue times below UN’s 30-minute threshold.

---

##  Tools & Techniques Used

- SQL aggregation (`GROUP BY`, `COUNT`, `SUM`, `AVG`)
- Window functions (`RANK()`, `DENSE_RANK()`, `ROW_NUMBER()`)
- DateTime functions (`DAYNAME()`, `TIME_FORMAT()`, `HOUR()`)
- Conditional logic (`CASE WHEN`)
- Pivot-style transformation using SQL
- Markdown reporting for stakeholder communication

---

##  Next Steps

- Integrate cost estimates for repairs and upgrades
- Visualize queue time patterns and source rankings
- Map contamination sources and infrastructure dependencies
- Prepare dispatch schedules and resource plans for rural deployment

---

##  Acknowledgments

This work is led by myself **Rediet**, a third-year Economics student and data analyst committed to solving real-world development challenges with strategic thinking, SQL mastery, and stakeholder empathy shaped this impactful analysis.

