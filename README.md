# HR Employee Attrition Dashboard

**Tools:** Power BI · DAX

## What This Project Does

Built an interactive Power BI dashboard to analyze employee attrition — which departments and job roles have the highest turnover, how income relates to attrition, and giving HR a way to filter and explore the data live rather than reading a static report.

## Dataset

- **Source:** [IBM HR Analytics Employee Attrition Dataset (Kaggle)](https://www.kaggle.com/datasets/pavansubhasht/ibm-hr-analytics-attrition-dataset)
- **Size:** 1,470 employee records, 35 attributes (Age, Department, JobRole, MonthlyIncome, Attrition, etc.)
- Dataset was already clean — no missing values or duplicates, so no ETL step was needed here (unlike the SQL project).

## Dashboard Features

**KPI Cards (top row)**
- Attrition Rate %
- Total Employees
- Employees Left
- Average Age of Leavers

**Visuals**
- Donut chart — overall attrition split (stayed vs. left)
- 100% stacked bar chart — attrition proportion by department
- Clustered bar chart — attrition count by job role
- Clustered column chart — average monthly income, stayed vs. left

**Interactivity**
- Slicers for Department and Gender — all visuals and KPIs update live based on selection

## DAX Measures Used

```dax
Attrition Rate % = 
DIVIDE(
    CALCULATE(COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition'), 'WA_Fn-UseC_-HR-Employee-Attrition'[Attrition] = "Yes"),
    COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition')
) * 100

Total Employees = COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition')

Employees Left = 
CALCULATE(
    COUNTROWS('WA_Fn-UseC_-HR-Employee-Attrition'),
    'WA_Fn-UseC_-HR-Employee-Attrition'[Attrition] = "Yes"
)

Avg Age of Leavers = 
CALCULATE(
    AVERAGE('WA_Fn-UseC_-HR-Employee-Attrition'[Age]),
    'WA_Fn-UseC_-HR-Employee-Attrition'[Attrition] = "Yes"
)
```

## Key Findings

- Overall attrition rate is **16.1%** (237 of 1,470 employees).
- **Sales Executive** has the highest attrition count among job roles, followed by Software Engineer and Marketing Executive.
- Employees who left had a **lower average monthly income** than those who stayed — income appears to be a factor in attrition.
- Attrition proportion varies noticeably by department, with Sales showing a higher share of departures relative to its headcount than R&D.

## Files in This Repository

| File | Contents |
|---|---|
| `hr-attrition-powerbi-dashboard.pbix` | The Power BI file — data model, DAX measures, and report |
| `dashboard_screenshot.png` | Screenshot of the dashboard for quick viewing without opening Power BI |

## Skills Covered

Power BI, DAX, data modeling, interactive dashboard design, business analysis# 
