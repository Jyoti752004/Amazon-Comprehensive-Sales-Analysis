# 📊 Amazon Comprehensive Sales Analysis Dashboard

![Power BI](https://img.shields.io/badge/Power%20BI-F2C811?style=for-the-badge&logo=powerbi&logoColor=black)
![Python](https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white)
![Pandas](https://img.shields.io/badge/Pandas-150458?style=for-the-badge&logo=pandas&logoColor=white)
![Jupyter](https://img.shields.io/badge/Jupyter-F37626?style=for-the-badge&logo=jupyter&logoColor=white)

---

## 📁 Project Overview

An end-to-end Data Analytics project analyzing Amazon sales data from **2011 to 2014**. The project covers the complete pipeline — from raw data ingestion and Python-based preprocessing to a fully interactive 4-page Power BI dashboard with a custom light pastel theme.

---

## 📂 Project Structure

```
Amazon-Sales-Dashboard/
│
├── Amazon_2_Raw.xlsx          # Raw dataset (original Excel file)
├── preProcessing.ipynb        # Python data cleaning notebook
├── Amazon_2_Cleaned.csv       # Cleaned dataset (output of preprocessing)
├── Dashboard_pdf.pdf          # PDF export of all 4 dashboard pages
└── README.md                  # Project documentation
```

---

## 🗂️ Dataset Information

| Property | Details |
|---|---|
| Source | Amazon Sales Data (2011–2014) |
| Raw File | Amazon_2_Raw.xlsx |
| Rows | 3,203 records |
| Columns | 10 features |
| Date Range | January 2011 – December 2014 |

### Columns

| Column | Type | Description |
|---|---|---|
| Order ID | String | Unique order identifier |
| Order Date | DateTime | Date order was placed |
| Ship Date | DateTime | Date order was shipped |
| EmailID | String | Customer email address |
| Geography | String | Country, City, State |
| Category | String | Product category |
| Product Name | String | Product name |
| Sales | Float | Sales amount ($) |
| Quantity | Float | Number of items ordered |
| Profit | Float | Profit amount ($) |

---

## 🧹 Data Preprocessing (Python)

**File:** `preProcessing.ipynb`

**Steps performed:**

1. Loaded raw Excel file using `pandas.read_excel()`
2. Explored data using `df.head()`, `df.describe()`, `df.info()`
3. Fixed data type — converted `Quantity` from `int64` → `float64`
4. Checked for duplicates → **0 duplicates found** ✅
5. Checked for null values → **0 null values found** ✅
6. Exported clean data → `Amazon_2_Cleaned.csv`

**Libraries used:**
```python
import pandas as pd
```

---

## 📊 Power BI Dashboard

**File:** `Amazon_sales_analysis.pbix`

The dashboard has **4 interactive pages** with synchronized slicers (Order Date & Category) across all pages.

---

### Page 1 — Overview

**KPI Cards:**
- Total Sales: **$725.5K**
- Total Profit: **$108.4K**
- Total Orders: **1,611**
- Avg Profit Margin: **21.95%**

**Charts:**
- Total Sales by Year (Combo chart — bars + orange trend line)
- Total Sales by Month (Area chart)
- Avg Order Size by Year (Column chart)
- Avg Order Value (AOV) Over Time (Line chart)

**Key Insights:**
- Sales grew **69%** from 2011 to 2014
- AOV dipped to **$414** in 2012, recovered to **$463** by 2014
- **November** is the peak sales month

---

### Page 2 — Product Performance

**KPI Cards:**
- Total Sales: $725.5K (Chair leads: $101.8K)
- Total Profit: $108.4K (Copiers: 38.8% margin)
- Total Orders: 1,611 (Binders most ordered: 403)
- Avg Profit Margin: 21.95% (Envelopes best: 46.4%)

**Charts:**
- Top 10 Best Selling Product Category (Horizontal bar chart)
- Avg Profit Margin by Product Category (Horizontal bar chart with negative values)
- Detailed Product Profitability Report (Table)

**Key Insights:**
- **Chairs** is the top selling category at $101.8K
- **Envelopes** has the best profit margin at **46.4%**
- **Bookcases (-4.6%)** and **Machines (-1.5%)** are loss-making categories ⚠️
- **Copiers** generated highest profit ($19,327) with only 25 orders

---

### Page 3 — Regional Performance

**KPI Cards:**
- Total Sales: $725.5K (Los Angeles leads: $176K)
- Total Profit: $108.4K (California leads: $76,381)
- Total Orders: 1,611 (Top 3 states: 87% orders)
- Top City: **Los Angeles** ($175.9K in sales)

**Charts:**
- Total Sales by City (Horizontal bar chart)
- Total Profit by State (Horizontal bar chart)
- Sales by State (Interactive bubble map)

**Key Insights:**
- **California** dominates with **63% of total revenue** ($457K) — geographic concentration risk!
- **Los Angeles** is the top city at $175.9K
- Top 3 states (CA, WA, NV) account for **87% of all orders**

---

### Page 4 — Operational Efficiency

**KPI Cards:**
- Avg Order-to-Ship: **3.93 days**
- Orders Over 3 Days: **66.19%** (2,120 orders)
- Total Orders: **1,611**
- On-time Orders: **33.81%** (1,083 within 3 days)

**Charts:**
- Longest Avg Shipping by State (Horizontal bar chart)
- Orders by Shipping Duration (Donut chart)
- Orders Over 3 Days by State (Horizontal bar chart)

**Key Insights:**
- **66.19%** of orders take more than 3 days to ship ⚠️
- **Wyoming** has the worst shipping time at **5 days**
- Only **33.81%** of orders are delivered on time
- California has the highest late shipment count at **1,314 orders**

---

## 🎨 Design Highlights

| Element | Details |
|---|---|
| Theme | Custom light pastel theme |
| Page background | #F0F2F8 |
| Card background | #FFFFFF |
| Amazon accent | #FF9900 (orange) |
| Sales KPI | #EEF3FF (blue tint) |
| Profit KPI | #EDFAF3 (green tint) |
| Orders KPI | #FFF3E8 (orange tint) |
| Margin KPI | #F3EEFF (purple tint) |
| Chart bars | #2A78D6 (primary) / #BFCFFF (secondary) |
| Trend line | #FF9900 (orange dashed) |
| Alert/negative | #E34948 (red) |

---

## 🛠️ Tools & Technologies

| Tool | Purpose |
|---|---|
| Python 3 | Data preprocessing |
| Pandas | Data manipulation & cleaning |
| Jupyter Notebook | EDA & validation |
| Power BI Desktop | Dashboard & visualization |
| DAX | Custom measures & calculations |
| Power Query | Data transformation in Power BI |
| Microsoft Clipchamp | Dashboard video walkthrough |

---

## 📈 DAX Measures Used

```dax
-- Average Profit Margin
Avg Profit Margin = AVERAGEX(
    'Amazon_2_Cleaned',
    DIVIDE('Amazon_2_Cleaned'[Profit],
           'Amazon_2_Cleaned'[Sales], 0)
)

-- Average Order Value
AOV = DIVIDE(SUM('Amazon_2_Cleaned'[Sales]),
             DISTINCTCOUNT('Amazon_2_Cleaned'[Order ID]), 0)

-- Shipping Days
Shipping_days = DATEDIFF('Amazon_2_Cleaned'[Order Date],
                          'Amazon_2_Cleaned'[Ship Date], DAY)

-- Orders Over 3 Days %
Orders Over 3 Days % = DIVIDE(
    COUNTROWS(FILTER('Amazon_2_Cleaned',
        'Amazon_2_Cleaned'[Shipping_days] > 3)),
    COUNTROWS('Amazon_2_Cleaned'), 0)
```

---

## 🚀 How to Run

### Prerequisites
- Python 3.x
- Jupyter Notebook
- Power BI Desktop (free download from Microsoft)

### Steps

1. **Clone or download** this repository

2. **Run preprocessing notebook:**
```bash
jupyter notebook preProcessing.ipynb
```
This generates `Amazon_2_Cleaned.csv`

3. **Open Power BI dashboard:**
- Open `Amazon_sales_analysis.pbix` in Power BI Desktop
- Refresh data source if needed

4. **Explore the dashboard:**
- Use date slicer to filter by year range
- Use category slicer to filter by product category
- Navigate between 4 pages using the sidebar

---

## 💡 Key Business Recommendations

1. **Geographic Risk** — California accounts for 63% of revenue. Expand to other states to reduce dependency.

2. **Loss-making Categories** — Bookcases and Machines are generating losses. Review pricing strategy or discontinue.

3. **Shipping Efficiency** — 66% of orders exceed 3-day delivery. Improve logistics especially in Wyoming, Montana, New Mexico.

4. **High Margin Opportunities** — Envelopes (46.4%) and Paper (45.5%) have excellent margins. Increase marketing for these categories.

5. **AOV Recovery** — AOV dropped in 2012 but recovered. Monitor pricing strategy to maintain upward trend.

---

## 👩‍💻 Author

**Jyoti**
Data Analyst — Altrodav Technologies (PlaceMux Platform)

---

## 📄 License

This project is for educational and portfolio purposes.
