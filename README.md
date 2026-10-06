<div align="center">

# 📊 Sales Data Analysis & Interactive Dashboard

**From 26K raw sales records to validated data, clear KPIs, and business-ready insights**

![Python](https://img.shields.io/badge/Python-3.10+-3776AB?logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Cleaning-150458?logo=pandas&logoColor=white)
![NumPy](https://img.shields.io/badge/NumPy-Validation-013243?logo=numpy&logoColor=white)
![Power BI](https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?logo=powerbi&logoColor=black)
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
- [Feature Engineering](#-feature-engineering)
- [Dashboard](#-dashboard)
- [Key Insights](#-key-insights)
- [Recommendations](#-recommendations)
- [Repository Structure](#-repository-structure)
- [How to Run](#-how-to-run)
- [Author](#-author)

---

## 🎯 Project Overview

This project takes a raw sales fact table (`FactSale.csv`) through a complete analytics pipeline: **validation → cleaning → feature engineering → KPI design → interactive dashboard → business insights**.

Before any analysis, every financial field was **re-calculated and verified** (revenue, tax, totals, quantities) so the numbers behind the dashboard can be trusted. The final dashboard turns **26,397 sale line items** across **3+ years (2013 to May 2016)** into clear answers about revenue, profit, products, and order behavior.

## 💼 Business Objectives

- Make sure the data is **accurate, consistent, and trustworthy** before analysis
- Track the **core KPIs**: revenue, profit, profit margin, and order volume
- Identify the **products and categories** that drive the business
- Understand **order-size behavior** and its contribution to revenue
- Uncover **time-based trends** in profit and revenue
- Deliver **actionable recommendations** backed by data

## 🗂 Dataset

| Property | Details |
|---|---|
| **File** | `FactSale.csv` (sales fact table) |
| **Rows** | 26,397 sale line items |
| **Columns** | 21 raw columns (20 after cleaning, plus engineered features) |
| **Period covered** | 2013 to 31 May 2016 |
| **Grain** | One row per invoice line item |

**Main fields:** `Sale Key`, `Customer Key`, `Stock Item Key`, `Invoice Date Key`, `Delivery Date Key`, `Description`, `Package`, `Quantity`, `Unit Price`, `Tax Rate`, `Total Excluding Tax`, `Tax Amount`, `Total Including Tax`, `Profit`, `Total Dry Items`, `Total Chiller Items`

## 🛠 Tech Stack

| Purpose | Tools |
|---|---|
| Language | Python |
| Data cleaning & validation | Pandas, NumPy |
| Environment | Jupyter Notebook |
| Dashboard | Power BI |

## 🔄 Workflow

```
Raw Data → Validation → Cleaning → Feature Engineering → KPIs → Dashboard → Insights
```

1. **Data Understanding:** reviewed structure, types, and null counts (`df.info()`)
2. **Validation:** checked duplicates, recalculated all financial fields, and tested business rules
3. **Cleaning:** fixed data types, trimmed text, flagged missing deliveries, handled placeholder customers, dropped a constant ETL column
4. **Feature Engineering:** added date parts, profit margin, loss flag, order-size buckets, customer type, and product category
5. **Dashboard:** built KPIs and visuals on the cleaned dataset
6. **Insights:** translated findings into business recommendations

## 🧹 Data Quality Report

| # | Check / Issue | Finding | How It Was Handled |
|---|---|---|---|
| 1 | **Duplicates** (full-row and `Sale Key`) | 0 found | No action needed |
| 2 | **Date columns stored as text** | `Invoice Date Key` and `Delivery Date Key` were `object` type | Converted to `datetime` (`%m/%d/%Y`) |
| 3 | **Missing delivery dates** | 13 rows, all invoiced on **31 May 2016** (last day of the data) | Not imputed. Flagged with a `Delivery Status` column (`Pending` / `Delivered`), since these are genuinely undelivered orders, not bad data |
| 4 | **Placeholder customers** (`Customer Key = 0`) | 9,077 rows (**34.39%**) | Labeled as `Unknown/Walk-in Customer` and tagged in `Customer Type` instead of dropping or guessing |
| 5 | **Constant ETL column** (`Lineage Key`) | Single value (11) in every row | Dropped, as it adds no analytical value |
| 6 | **Text formatting** (`Description`, `Package`) | Possible stray whitespace | Trimmed. Package types verified: `Each`, `Packet`, `Pair`, `Bag` |
| 7 | **Revenue math** (`Quantity × Unit Price`) | 0 mismatches | ✅ Pass |
| 8 | **Tax amount** (rate × net, round-half-up) | 0 mismatches | ✅ Pass |
| 9 | **Total including tax** (net + tax) | 0 mismatches | ✅ Pass |
| 10 | **Quantity balance** (Dry + Chiller items = Quantity) | 0 mismatches | ✅ Pass |
| 11 | **Negative profit** | 566 rows (**2.14%**). 492 of them share the exact same margin (−5.56%), suggesting a repeatable pricing pattern rather than random errors | Kept as real business data and flagged with `Is_Loss_Sale` |
| 12 | **Delivery lag** | Every delivered order shipped exactly **1 day** after invoicing | ✅ Consistent. No exceptions |
| 13 | **Outliers** (per-product IQR) | 74 unit-price outliers (0.28%) and 4 quantity outliers (0.02%) | Kept, since they are a negligible share and plausible for sales data |

> **Missing values:** the only nulls in the dataset were the 13 delivery dates above, so no statistical imputation was needed.

## 🧩 Feature Engineering

| New Column | Logic |
|---|---|
| `Invoice Year`, `Quarter`, `Month`, `Month Name`, `Day of Week` | Extracted from the invoice date |
| `Profit Margin %` | `Profit / Total Excluding Tax` |
| `Is_Loss_Sale` | `True` when `Profit < 0` |
| `Order Size` | **Small** (≤ 10 units), **Medium** (11 to 60), **Large** (61+) |
| `Customer Type` | `Known` vs `Unknown/Walk-in` |
| `Delivery Status` | `Delivered` vs `Pending` |
| `Product_Category` | Keyword matching on `Description` into 6 categories: Packaging & Shipping Supplies, Apparel & Wearables, Toys & Seasonal, General Merchandise, Electronics & Accessories, Drinkware & Novelty |

## 📈 Dashboard

![Sales Dashboard](images/dashboard.png)

**KPIs:**

| Metric | Value |
|---|---|
| 💰 Total Revenue | **~$20M** |
| 📈 Total Profit | **$9.92M** |
| 🧾 Total Orders | **8.19K** |
| 🎯 Profit Margin | **~50%** (profit ÷ revenue) |

**Visuals:**
- **Order Size Distribution:** count of sales by Small / Medium / Large orders
- **Total Revenue by Product Category:** which categories drive the business
- **Monthly Profit Trend:** profit by year and month (Jan 2013 to 2016)

## 💡 Key Insights

1. **📈 Steady growth, then a slowdown.** Revenue grew every full year from 2013 to 2015 (**$5.26M → $5.84M → $6.35M, +20.7%** overall). The 5 completed months of 2016 ($2.43M) annualize to about **$5.83M**, which is below 2015's pace.

2. **📦 One category dominates.** *Packaging & Shipping Supplies* alone brings in **58.1% of total revenue ($11.5M)**, nearly **6× the next-largest category**, Apparel & Wearables (21.3%). The business is highly concentrated.

3. **🛒 A quarter of orders drive half the revenue.** *Large* orders (61+ units) are only **23.8% of line items** but generate **49.8% of revenue**.

4. **🚚 Flawless fulfillment.** **26,384 of 26,397** orders shipped exactly **one day** after invoicing, with zero exceptions across 3+ years. The only 13 unfulfilled orders were all dated on the very last day of the dataset.

5. **🔍 Profit is seasonal and volatile.** Monthly profit swings between roughly **$160K and $300K**, with repeated peaks and dips each year, which points to a seasonal sales cycle.

6. **⚠️ Small but systematic losses.** 2.14% of sales lose money, and most of them (492 of 566) share the same −5.56% margin, which suggests a specific pricing or discount rule worth reviewing.

7. **👤 Weak customer visibility.** 34.39% of sales come from unknown / walk-in customers, which limits customer-level analysis.

## ✅ Recommendations

- **Diversify revenue:** reduce dependence on Packaging & Shipping Supplies by growing Apparel, Toys, and Electronics
- **Protect large orders:** offer bulk-order incentives and account management, as they generate half the revenue
- **Investigate the loss-making pattern:** review the pricing or discount rule behind the repeated −5.56% margin
- **Plan for seasonality:** align inventory and promotions with profit peaks and troughs
- **Improve customer capture:** collect customer IDs at checkout to enable retention and segmentation analysis
- **Monitor the 2016 slowdown:** track monthly revenue against 2015 to confirm whether growth is stalling

## 📁 Repository Structure

```
sales_data_analysis/
│
├── Data_Files/
│   ├── Raw_Files/
│   │   └── FactSale.csv              # Raw dataset
│   └── Cleaned_files/
│       └── cleaned_sales.csv         # Cleaned + engineered dataset
│
├── sales_data_analysis.ipynb         # Cleaning, validation & feature engineering
├── images/
│   └── dashboard.png                 # Dashboard screenshot
└── README.md
```

## 🚀 How to Run

```bash
# 1. Clone the repository
git clone https://github.com/kirlosmagdy/sales_data_analysis.git
cd sales_data_analysis

# 2. Install dependencies
pip install pandas numpy jupyter

# 3. Open the notebook
jupyter notebook sales_data_analysis.ipynb
```

> ⚠️ Update the file paths inside the notebook (`pd.read_csv(...)` and `df.to_csv(...)`) to match your local folder before running.

## 👤 Author

**Kirolos Magdy**: Data Engineer | Analytics Engineer
Faculty of Computers and Data Science, Alexandria University

[![GitHub](https://img.shields.io/badge/GitHub-kirlosmagdy-181717?logo=github)](https://github.com/kirlosmagdy)
[![LinkedIn](https://img.shields.io/badge/LinkedIn-Kirolos%20Magdy-0A66C2?logo=linkedin)](https://linkedin.com/in/kirolos-magdy1/)

---

<div align="center">

⭐ If you found this project useful, consider giving it a star!

</div>
