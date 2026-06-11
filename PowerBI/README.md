# Power BI Dashboards

## How to Connect Power BI to MySQL

1. Open Power BI Desktop
2. Click **Get Data → MySQL Database**
3. Server: `localhost`, Database: `employees`
4. Import the SQL query output from each `.sql` file as a named query

## Dashboard Pages to Build

### Page 1: Workforce Overview
**Visuals:**
- KPI cards: Total Headcount, % Female, Avg Age, Avg Tenure
- Bar chart: Headcount by Department
- Donut chart: Gender split company-wide
- Clustered bar: Gender split by department (stacked %)
- Column chart: Age band distribution

**SQL queries used:**
- `sql/01_workforce/headcount_by_dept.sql`
- `sql/01_workforce/gender_distribution.sql`
- `sql/01_workforce/age_distribution.sql`

---

### Page 2: Attrition & Retention
**Visuals:**
- KPI cards: Overall Attrition Rate, Avg Tenure at Exit, Flight Risk Count
- Line chart: Attrition rate by year and department
- Horizontal bar: Avg tenure at exit by department (sorted ascending)
- Table with conditional formatting: Flight risk employees list

**SQL queries used:**
- `sql/02_attrition/annual_attrition_rate.sql`
- `sql/02_attrition/avg_tenure_at_exit.sql`
- `sql/02_attrition/flight_risk_employees.sql`

---

### Page 3: Salary Analytics
**Visuals:**
- KPI cards: Company Avg Salary, Highest Dept Avg, Lowest Dept Avg
- Bar chart: Avg salary by department
- Diverging bar: Gender pay gap by department (centered at 0)
- Line chart: YoY salary growth trend by department
- Table: Top 10% earners with department and title

**SQL queries used:**
- `sql/03_salary/salary_by_department.sql`
- `sql/03_salary/gender_pay_gap.sql`
- `sql/03_salary/salary_yoy_growth.sql`
- `sql/03_salary/top_earners.sql`

---

### Page 4: Tenure & Promotion
**Visuals:**
- KPI cards: Avg Tenure (current staff), Avg Time to First Promotion
- 100% stacked bar: Tenure band distribution by department
- Horizontal bar: Avg time to first promotion by department

**SQL queries used:**
- `sql/04_tenure/time_to_first_promotion.sql`
- `sql/04_tenure/tenure_distribution.sql`

---

### Page 5: Management & Hiring
**Visuals:**
- Table: Manager span of control with team size and avg salary
- Scatter plot: Manager salary vs team avg salary (pay ratio)
- Line chart: Monthly hiring trend (by year)
- Clustered bar: New hire vs existing staff salary comparison

**SQL queries used:**
- `sql/05_management/manager_span_of_control.sql`
- `sql/05_management/manager_vs_team_pay_ratio.sql`
- `sql/06_hiring/monthly_hiring_trend.sql`
- `sql/06_hiring/new_hire_vs_benchmark_salary.sql`

---

## Recommended DAX Measures

```dax
-- Attrition Rate %
Attrition Rate = DIVIDE([Total Exits], [Total Headcount], 0) * 100

-- Gender Pay Gap %
Gender Pay Gap % = 
DIVIDE(
    [Avg Male Salary] - [Avg Female Salary],
    [Avg Male Salary],
    0
) * 100

-- Pay Ratio
Pay Ratio = DIVIDE([Manager Salary], [Team Avg Salary], 0)
```
