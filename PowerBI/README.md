Power BI Dashboards
How to Connect Power BI to MySQL
Open Power BI Desktop
Click Get Data → MySQL Database
Server: `localhost`, Database: `employees`
Import the SQL query output from each `.sql` file as a named query
Dashboard Pages to Build
Page 1: Workforce Overview
Visuals:
KPI cards: Total Headcount, % Female, Avg Age, Avg Tenure
Bar chart: Headcount by Department
Donut chart: Gender split company-wide
Clustered bar: Gender split by department (stacked %)
Column chart: Age band distribution
SQL queries used:
`sql/01\_workforce/headcount\_by\_dept.sql`
`sql/01\_workforce/gender\_distribution.sql`
`sql/01\_workforce/age\_distribution.sql`
---
Page 2: Attrition & Retention
Visuals:
KPI cards: Overall Attrition Rate, Avg Tenure at Exit, Flight Risk Count
Line chart: Attrition rate by year and department
Horizontal bar: Avg tenure at exit by department (sorted ascending)
Table with conditional formatting: Flight risk employees list
SQL queries used:
`sql/02\_attrition/annual\_attrition\_rate.sql`
`sql/02\_attrition/avg\_tenure\_at\_exit.sql`
`sql/02\_attrition/flight\_risk\_employees.sql`
---
Page 3: Salary Analytics
Visuals:
KPI cards: Company Avg Salary, Highest Dept Avg, Lowest Dept Avg
Bar chart: Avg salary by department
Diverging bar: Gender pay gap by department (centered at 0)
Line chart: YoY salary growth trend by department
Table: Top 10% earners with department and title
SQL queries used:
`sql/03\_salary/salary\_by\_department.sql`
`sql/03\_salary/gender\_pay\_gap.sql`
`sql/03\_salary/salary\_yoy\_growth.sql`
`sql/03\_salary/top\_earners.sql`
---
Page 4: Tenure & Promotion
Visuals:
KPI cards: Avg Tenure (current staff), Avg Time to First Promotion
100% stacked bar: Tenure band distribution by department
Horizontal bar: Avg time to first promotion by department
SQL queries used:
`sql/04\_tenure/time\_to\_first\_promotion.sql`
`sql/04\_tenure/tenure\_distribution.sql`
---
Page 5: Management & Hiring
Visuals:
Table: Manager span of control with team size and avg salary
Scatter plot: Manager salary vs team avg salary (pay ratio)
Line chart: Monthly hiring trend (by year)
Clustered bar: New hire vs existing staff salary comparison
SQL queries used:
`sql/05\_management/manager\_span\_of\_control.sql`
`sql/05\_management/manager\_vs\_team\_pay\_ratio.sql`
`sql/06\_hiring/monthly\_hiring\_trend.sql`
`sql/06\_hiring/new\_hire\_vs\_benchmark\_salary.sql`
---
Recommended DAX Measures
```dax
-- Attrition Rate %
Attrition Rate = DIVIDE(\[Total Exits], \[Total Headcount], 0) \* 100

-- Gender Pay Gap %
Gender Pay Gap % = 
DIVIDE(
    \[Avg Male Salary] - \[Avg Female Salary],
    \[Avg Male Salary],
    0
) \* 100

-- Pay Ratio
Pay Ratio = DIVIDE(\[Manager Salary], \[Team Avg Salary], 0)
```
