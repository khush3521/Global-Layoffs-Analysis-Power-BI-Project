# 🌍 Global Layoffs Analysis — Power BI Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![DAX](https://img.shields.io/badge/DAX-005C84?style=for-the-badge)
![Data Modeling](https://img.shields.io/badge/Data%20Modeling-brightgreen?style=for-the-badge)
![Status](https://img.shields.io/badge/Project-Completed-success?style=for-the-badge)

> 🏢 Multiple industries & countries | 📉 2020–2023 workforce reduction trends | 📊 YoY growth analysis

---

## 📊 End-to-End Analytics Pipeline

```
Raw Layoffs Data (CSV) → Power Query (Cleaning) → Data Modeling → DAX (KPIs & YoY) → Power BI Dashboard → Strategic Insights
```

---

## 📌 Project Overview

Between 2020 and 2023, the global workforce experienced unprecedented disruption — from pandemic-driven cuts to post-hiring-boom corrections in tech. But which industries were hit hardest? Which countries saw the sharpest spikes? And are layoffs slowing down or accelerating?

This project builds a **2-page interactive Power BI dashboard** to answer those questions — combining time series analysis, country-level breakdowns, industry segmentation, and YoY growth tracking into an executive-ready report.

---

## 🎯 Business Objectives

1. **When did layoffs peak** — and are we past the worst?
2. **Which industries carry the highest workforce risk?**
3. **Which countries and companies drove the most cuts?**
4. **How does YoY growth reveal acceleration or recovery patterns?**

---

## 📷 Dashboard Preview

### 📌 Page 1 — Executive Overview
[![Executive Overview](Screenshot%202026-01-16%20140403.png)](https://github.com/khush3521/Global-Layoffs-Analysis-Power-BI-Project/blob/main/Screenshot%202026-01-16%20140403.png)

### 📌 Page 2 — Deep Analysis
[![Deep Analysis](Screenshot%202026-01-16%20140622.png)](https://github.com/khush3521/Global-Layoffs-Analysis-Power-BI-Project/blob/main/Screenshot%202026-01-16%20140622.png)

---

## 📈 Key Insights & Business Impact

| Finding | Implication |
|---|---|
| **2020 and 2022 saw the sharpest layoff spikes** | Two distinct crises — COVID cuts and post-boom tech correction |
| **Technology sector had the highest total layoffs** | Over-hiring during 2020–2021 created a correction bubble |
| **USA accounts for the majority of global layoffs** | Concentration risk — US tech dominance amplifies global numbers |
| **YoY growth highlights rapid acceleration in late 2022** | Early warning signal — companies were reacting to rate hikes |
| **A small number of large companies drove outsized volume** | Meta, Amazon, Google layoffs skewed industry-level averages |

---

## 📊 Dashboard Structure

### 🔹 Page 1 — Executive Overview
High-level summary for leadership and HR strategists:
- **Total Layoffs** — global workforce reduction at a glance
- **Companies Impacted** — breadth of the crisis
- **Average Layoff %** — severity per company
- **Time Series Analysis** — monthly & yearly trend lines
- **Top 10 Countries** — geographic concentration of cuts
- **Interactive Slicers** — filter by Country, Year, Location

### 🔹 Page 2 — Deep Analysis
Granular breakdown for analysts and industry researchers:
- **Industry-wise Distribution** — which sectors were hit hardest
- **Company-level Analysis** — top companies by total layoffs
- **Year-over-Year (YoY) Growth** — acceleration and deceleration patterns
- **Layoffs with Known Dates** — data completeness indicator

---

## 🧠 DAX Measures

```DAX
-- Total Layoffs
Total Layoffs = SUM(layoffs[total_laid_off])

-- Companies Impacted
Companies Impacted = DISTINCTCOUNT(layoffs[company])

-- Average Layoff Percentage
Avg Layoff % = AVERAGE(layoffs[percentage_laid_off])

-- Layoffs with Known Dates
Known Date Layoffs =
CALCULATE(
    [Total Layoffs],
    NOT ISBLANK(layoffs[date])
)

-- YoY Layoff Growth
YoY Growth % =
VAR CurrentYear =
    CALCULATE([Total Layoffs], YEAR(layoffs[date]) = SELECTEDVALUE(layoffs[Year]))
VAR PriorYear =
    CALCULATE([Total Layoffs], YEAR(layoffs[date]) = SELECTEDVALUE(layoffs[Year]) - 1)
RETURN
    DIVIDE(CurrentYear - PriorYear, PriorYear)

-- Running Total (Cumulative Layoffs)
Cumulative Layoffs =
CALCULATE(
    [Total Layoffs],
    FILTER(
        ALL(layoffs[date]),
        layoffs[date] <= MAX(layoffs[date])
    )
)

-- Top Country Share
USA Share % =
DIVIDE(
    CALCULATE([Total Layoffs], layoffs[country] = "United States"),
    [Total Layoffs]
)

-- Industry Rank by Layoffs
Industry Rank =
RANKX(
    ALL(layoffs[industry]),
    [Total Layoffs],
    ,
    DESC,
    DENSE
)
```

---

## 🛠 Tools & Technologies

| Tool | Purpose |
|------|---------|
| Power BI Desktop | 2-page interactive dashboard |
| DAX | KPIs, YoY growth, cumulative trends, ranking |
| Power Query | Data cleaning, date standardization, null handling |
| CSV / Excel | Raw layoffs dataset |

---

## 📂 Dataset Attributes

| Column | Description |
|---|---|
| Company | Company name |
| Industry | Sector / industry category |
| Country | Country where layoffs occurred |
| Location | City / region |
| Total Laid Off | Number of employees laid off |
| Percentage Laid Off | % of workforce cut |
| Date | Date of layoff announcement |
| Stage | Company funding stage (Series A, IPO, etc.) |
| Funds Raised | Total capital raised by company |

---

## 📂 Repository Structure

```
Global-Layoffs-Analysis-Power-BI-Project/
│
├── data/
│   └── layoffs_data.csv
│
├── powerbi/
│   └── Global_Layoffs_Dashboard.pbix
│
├── Screenshot 2026-01-16 140403.png     ← Page 1 preview
├── Screenshot 2026-01-16 140622.png     ← Page 2 preview
└── README.md
```

> 💡 **Tip:** Rename screenshots to `page1_executive_overview.png` and `page2_deep_analysis.png` for a cleaner repo.

---

## 🔮 Future Improvements

- Add **Python EDA** — correlation between funds raised and layoff severity
- Build **predictive model** for layoff probability by industry + funding stage
- Add **company funding stage breakdown** — are early-stage or late-stage firms cutting more?
- Integrate **live data feed** from layoffs.fyi for real-time dashboard updates
- Publish to **Power BI Service** for web sharing

---

## 👨‍💻 Author

**Khush Panchal** — Data Analyst
Specializing in business intelligence, workforce analytics & data storytelling

[![LinkedIn](https://img.shields.io/badge/LinkedIn-Connect-blue?style=flat&logo=linkedin)](https://www.linkedin.com/in/khush-panchal-96b557352)
[![GitHub](https://img.shields.io/badge/GitHub-Portfolio-black?style=flat&logo=github)](https://github.com/khush3521)

---

⭐ If you found this project valuable, please consider starring this repository!
