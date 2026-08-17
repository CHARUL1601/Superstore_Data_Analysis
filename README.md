# US Superstore Sales & Profitability Analysis
**An End-to-End Data Analytics Case Study by a Data Analyst**

---

## 📌 Project Overview
In this project, I analyzed four years of transaction data from a US retail superstore (**9,994 orders**, **$2.297M in revenue**, **$286.4K in net profit**) from 2015 to 2018. 

While top-line sales grew steadily (+51.4% over four years), my goal was to find where the business was losing money and uncover actionable opportunities to improve margins. Through data cleaning, exploratory analysis, and customer segmentation, I identified significant profit leakages from over-discounting, loss-making product categories, and regional pricing imbalances.

---

## 🎯 Executive KPI Summary

| Key Metric | Value | What It Means |
| :--- | :--- | :--- |
| **Total Revenue** | **$2,297,200.86** | Generated across 5,009 unique customer orders |
| **Net Operating Profit** | **$286,397.02** | Overall profit margin of **12.47%** |
| **The 20% Discount Cliff** | **-$135,376.06** | Total profit lost on transactions discounted over 20% |
| **Top Sub-Category Engine** | **Copiers (37.20% Margin)** | $55.6K profit generated from just 68 sales |
| **Biggest Money Loser** | **Tables (-8.56% Margin)** | Incurred -$17.7K in losses despite $206.9K in sales |
| **Top Region** | **West Region (14.94% Margin)** | Delivered $108.4K profit on $725.5K revenue |
| **Underperforming Region** | **Central Region (7.92% Margin)** | Dragged down by deep discounting in Texas (-$25.7K) and Illinois (-$12.6K) |
| **Customer Concentration** | **Top 38.7% (Champions/Loyalists)** | Generated **66.5% of total business profits** |

---

## 📁 Repository Structure

```
superstore/
├── Superstore.csv                            # Raw transaction data (9,994 rows, 21 columns)
│
├── 01_data_cleaning_and_preparation.ipynb    # Part 1: Schema audit, missing value fixes & feature engineering
├── cleaned_superstore.csv                    # Cleaned dataset with 13 engineered features
├── 02_business_insights_and_eda.ipynb        # Part 2: 5 Business questions, visualizations & recommendations
│
├── superstore_data_analysis.ipynb            # All-in-One Master Notebook (Combined workflow)
└── README.md                                 # Project documentation & summary
```

---

## 🔬 What I Did: Step-by-Step Breakdown

### Part 1: Data Cleaning & Preparation (`01_data_cleaning_and_preparation.ipynb`)
- **Missing Value Handling**: Only `Postal Code` had missing values (11 rows). I filtered for those rows and discovered they were all from **Burlington, Vermont**. Using official USPS data, I imputed Burlington's ZIP code (`05401`) and formatted it as a 5-digit string so leading zeros weren't lost.
- **Feature Engineering**:
  - `Profit Margin (%)` = `(Profit / Sales) * 100`
  - `Shipping Duration (Days)` = `Ship Date - Order Date`
  - `Discount Bracket` = 6 operational tiers (`0%`, `1-10%`, `11-20%`, `21-30%`, `31-50%`, `>50%`)
  - `Is Loss` = Flag for negative-margin transactions (`Profit < 0`)
  - `Unit Price` & `COGS`
  - Calendar fields (`Year`, `Month`, `Quarter`, `Day of Week`)
- **Export**: Saved the transformed data as `cleaned_superstore.csv`.

---

### Part 2: Business Questions & Strategic Insights (`02_business_insights_and_eda.ipynb`)

#### 1. Time Variation & Seasonality
- **Long-Term Trajectory**: Sales expanded by **+51.4%** from 2015 ($484.2K) to 2018 ($733.2K), maintaining positive double-digit YoY growth.
- **Q4 Surge**: November and December generate over **30% of total annual sales and profit** (3.2x higher than January/February lows).
- **Shipping Times**: Standard Class (59.1% of orders) averages 5.01 days, while First Class averages 2.18 days and Same Day fulfills in 0.04 days.

#### 2. Sales vs. Profit by Product (Stars vs. Drainers)
- **Category Comparison**: Technology (17.4% margin) and Office Supplies (17.0% margin) are consistent profit drivers, while Furniture struggles at just **2.49% margin**.
- **Top Earners**: **Copiers** delivered **$55.6K profit** (37.2% margin from 68 sales) and **Paper** delivered **$34.1K profit** (43.4% margin, 0 loss-making orders).
- **Loss Drainers**: **Tables** lost **-$17,725.48** (-8.56% margin) and **Bookcases** lost **-$3,472.56** (-3.02% margin).

#### 3. The Discount Dilemma & The 20% Cliff
- **The 20% Inversion Point**:
  - `0% Discount`: 29.51% margin ($320.9K profit).
  - `1% - 20% Discount`: 11.90% margin ($100.8K profit).
  - `21% - 30% Discount`: **-10.05% margin** (-$10.4K loss).
  - `31% - 50% Discount`: **-24.80% margin** (-$48.4K loss).
  - `> 50% Discount`: **-119.20% margin** (-$76.6K loss).
- **Profit Destroyed**: Discounts over 20% resulted in **$135,376.06 in cumulative losses** across 1,393 transactions (86.1% failure rate).

#### 4. Regional & State Performance
- **Regional Breakdown**: The West ($108.4K profit, 14.94% margin) and East ($91.5K profit, 13.48% margin) lead the business. The Central region generated $501.2K in sales but only **$39.7K in profit (7.92% margin)**.
- **Root Cause**: Heavy regional discounting in **Texas** (37.2% avg discount, -$25.7K loss) and **Illinois** (39.0% avg discount, -$12.6K loss), where over 50% of orders lost money.

#### 5. Customer RFM Segmentation
- **Value Concentration**: **Champions & Loyalists** (38.7% of customers) drove **66.5% of total profits** ($190.5K) with healthy 14.2% margins and minimal discount dependency.
- **At-Risk Cohort**: 178 customers ($478.4K past spend) haven't purchased in ~295 days. They received high discounts in the past (16.2% avg), showing they are deal-driven buyers who drop off without promotions.

---

## 💡 My Top 5 Strategic Recommendations

1. **Cap Standard Discounts at 20%**: Stop discounts over 20% to immediately protect over **$135K in profits**.
2. **End Blanket Coupon Codes in Texas and Illinois**: Switch from statewide coupon codes to targeted, SKU-level pricing to fix the Central region's margin.
3. **Restructure Furniture (Tables & Bookcases)**: Renegotiate freight contracts for bulky items, bundle Tables with high-margin Chairs/Accessories, and drop unprofitable SKUs.
4. **Give Champions Service Perks Instead of Price Cuts**: Our best customers aren't discount-sensitive. Offer them free priority shipping upgrades and dedicated support rather than cash markdowns.
5. **Lock in Carrier Capacity by September for Q4**: Plan warehouse staffing and carrier contracts in late Q3 to handle the holiday rush without expensive expedited surcharges.

---

## 🚀 How to Run

```bash
# 1. Install dependencies
pip install pandas numpy matplotlib seaborn

# 2. Run the pipeline
# Open '01_data_cleaning_and_preparation.ipynb' and Run All
# Open '02_business_insights_and_eda.ipynb' and Run All
```
