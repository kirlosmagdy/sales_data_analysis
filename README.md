<div align="center">

# 📊 Sales Data Analysis & Interactive Dashboard

**End-to-end Python project: from messy sales data to clean insights and a business-ready dashboard**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-150458?logo=pandas&logoColor=white)
![Plotly](https://img.shields.io/badge/Plotly-Interactive%20Charts-3F4F75?logo=plotly&logoColor=white)
![Status](https://img.shields.io/badge/Status-Completed-brightgreen)

</div>

---

## 📌 Table of Contents
- [Project Overview](#-project-overview)
- [Business Objectives](#-business-objectives)
- [Dataset](#-dataset)
- [Tech Stack](#-tech-stack)
- [Workflow](#-workflow)
- [Data Quality Report](#-data-quality-report)
- [Dashboard](#-dashboard)
- [Key Insights](#-key-insights)
- [Project Structure](#-project-structure)
- [How to Run](#-how-to-run)
- [Author](#-author)

---

## 🎯 Project Overview

Raw sales data is rarely ready for decision-making. This project takes a sales dataset (`FactSale.csv`) through a complete analytics pipeline: **validation → cleaning → imputation → exploratory analysis → KPI design → interactive dashboard**, all built in **Python**.

The goal is to turn transactional records into clear, actionable answers about revenue, product performance, and sales trends.

## 💼 Business Objectives

- Ensure the data is **accurate, consistent, and trustworthy** before analysis
- Track the **core sales KPIs** (revenue, quantity, average order value, growth)
- Identify **top-performing and underperforming** products, categories, and regions
- Uncover **time-based trends and seasonality**
- Deliver **business-focused recommendations** backed by data

## 🗂 Dataset

| Property | Details |
|---|---|
| **File** | `FactSale.csv` |
| **Type** | Sales fact table (transaction-level) |
| **Rows × Columns** | `[add number of rows]` × `[add number of columns]` |
| **Period covered** | `[add date range]` |

**Main fields:** `[list key columns, e.g. date, product, quantity, unit price, sales amount, customer/region]`

## 🛠 Tech Stack

| Purpose | Tools |
|---|---|
| Language | Python |
| Data manipulation | Pandas, NumPy |
| Visualization | Plotly, Matplotlib, Seaborn |
| Dashboard | `[Plotly Dash / Streamlit, adjust to what you used]` |
| Environment | Jupyter Notebook |

## 🔄 Workflow

```
Raw Data  →  Validation  →  Cleaning  →  Imputation  →  EDA  →  KPIs  →  Dashboard  →  Insights
```

1. **Data Understanding:** inspected structure, data types, ranges, and distributions
2. **Validation:** checked for duplicates, invalid values, inconsistent formats, and outliers
3. **Cleaning:** standardized data types and formats, removed duplicates, fixed inconsistencies
4. **Imputation:** handled missing values using methods suited to each column (median/mode/group-based)
5. **Exploratory Analysis:** analyzed trends, distributions, and relationships
6. **KPI Design:** defined metrics that matter to the business
7. **Dashboard:** built interactive visuals with filters for self-service exploration
8. **Insights:** translated findings into recommendations

## 🧹 Data Quality Report

| Issue Found | How It Was Handled |
|---|---|
| Missing values | `[e.g. median for numeric, mode for categorical]` |
| Duplicate records | `[e.g. removed exact duplicates]` |
| Inconsistent formats | `[e.g. standardized dates and text casing]` |
| Outliers / invalid values | `[e.g. flagged and treated using IQR]` |

> Update the table with the actual issues and counts from your notebook.

## 📈 Dashboard

> 📸 *Add a screenshot or GIF of your dashboard here:*
>
> `![Dashboard Preview](images/dashboard.png)`

**Key KPIs:**
- 💰 Total Sales / Revenue
- 📦 Total Quantity Sold
- 🧾 Average Order Value
- 📆 Monthly / Yearly Growth
- 🏆 Top Products & Categories

**Visuals included:** sales trend over time, top/bottom performers, category and regional breakdowns, and interactive filters.

## 💡 Key Insights

1. **`[Insight 1]`**: e.g. Sales peak in `[month/season]`, suggesting `[action]`
2. **`[Insight 2]`**: e.g. Top `[X]` products generate `[Y]%` of revenue
3. **`[Insight 3]`**: e.g. `[Region/category]` underperforms despite `[reason]`
4. **Recommendation:** `[one clear business action based on the findings]`

## 📁 Project Structure

```
sales_data_analysis/
│
├── data/
│   ├── FactSale.csv              # Raw dataset
│   └── cleaned_FactSale.csv      # Cleaned dataset
│
├── notebooks/
│   └── sales_analysis.ipynb      # Cleaning, EDA, and analysis
│
├── dashboard/
│   └── app.py                    # Interactive dashboard
│
├── images/                       # Dashboard screenshots
├── requirements.txt
└── README.md
```

> Adjust the tree to match your actual repository layout.

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/kirlosmagdy/sales_data_analysis.git
cd sales_data_analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Explore the analysis
jupyter notebook

# 4. Launch the dashboard
python dashboard/app.py
```

## 👤 Author

**Kirolos Magdy**: Data Engineer | Analytics Engineer
Faculty of Computers and Data Science, Alexandria University

[![GitHub](https://img.shields.io/badge/GitHub-kirlosmagdy-181717?logo=github)](https://github.com/kirlosmagdy)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Kirolos%20Magdy-0A66C2?logo=linkedin)](https://linkedin.com/in/kirolos-magdy1/)

---

<div align="center">

⭐ If you found this project useful, consider giving it a star!

</div>
