# Online Retail — Data Cleaning & Visualization with Pandas

An end-to-end exploratory data analysis project that takes a deliberately messy retail sales export, cleans it into an analysis-ready dataset, and turns it into a set of insights and a visual dashboard using **pandas**, **matplotlib**, and **seaborn**.

The goal of the project is to practice the full analyst workflow — not just plotting pretty charts, but making and defending the judgement calls that real-world dirty data forces on you.

---

## Overview

The raw dataset (`messy_retail.csv`) ships with a realistic set of data-quality problems baked in:

- Missing customer IDs and product descriptions
- Cancelled invoices (returns) mixed in with valid sales
- Stray negative quantities and zero / absurd unit prices
- Quantity outliers (genuine bulk orders vs. obvious typos)
- Inconsistent text casing and stray whitespace
- Three different date formats in a single column
- Exact duplicate and near-duplicate rows

The notebook works through cleaning each of these, then builds analyses and visualizations on top of the cleaned data.

---

## What's inside

| Stage | What it does |
| --- | --- |
| **Data audit** | A reusable `audit()` function that reports shape, dtypes, nulls, duplicates, numeric ranges, and a sample of raw values — run *before* any cleaning to document what's wrong. |
| **Cleaning** | Date parsing, missing-value handling, text standardization, separating returns from sales, removing duplicates, and filtering data-entry errors. |
| **Feature engineering** | Derived `Revenue`, `Year`, `Month`, `DayOfWeek`, and `Hour` columns. |
| **Analysis** | Top products and customers by revenue, monthly revenue trend, revenue by day-of-week and hour, and repeat-purchase rate. |
| **Dashboard** | A 2×2 matplotlib figure combining the monthly trend, top products, revenue by weekday, and order-value distribution. |
| **Heatmap** | A seaborn heatmap of revenue across day-of-week × hour to surface peak shopping windows. |
| **Seaborn reference** | Examples of bar, line, and count plots using seaborn's dataframe-first syntax. |

---

## Key decisions

A few cleaning choices worth calling out, since the *reasoning* matters more than the code:

- **Missing customer IDs** are flagged as `GUEST` rather than dropped — these are still valid transactions that count toward revenue and product analysis. They're excluded only from customer-level metrics (top customers, repeat rate).
- **Returns** (cancelled invoices) are split into a separate dataframe rather than deleted — returns are business signal, not noise.
- **Outliers** are filtered with explicit, defensible thresholds (e.g. dropping a 80,995-unit order as a typo) rather than blindly clipped.

---

## Tech stack

- **Python 3**
- **pandas** — cleaning, reshaping, groupby/pivot analysis
- **matplotlib** — multi-panel dashboard
- **seaborn** — heatmap and statistical charts
- **Jupyter Notebook**

---

## Getting started

1. Clone the repository:
   ```bash
   git clone https://github.com/<your-username>/<your-repo>.git
   cd <your-repo>
   ```

2. Install the dependencies:
   ```bash
   pip install pandas numpy matplotlib seaborn jupyter
   ```

3. Launch the notebook (keep `messy_retail.csv` in the same folder):
   ```bash
   jupyter notebook Pandas_Matplot_SNS.ipynb
   ```

4. Run the cells top to bottom — each phase builds on the previous one.

---

## Repository structure

```
.
├── Pandas_Matplot_SNS.ipynb   # main analysis notebook
├── messy_retail.csv           # raw (messy) dataset
└── README.md
```

---

## Skills demonstrated

Data cleaning · missing-value strategies · datetime parsing · groupby and pivot-table aggregation · feature engineering · exploratory data analysis · data visualization · dashboard design.

---

*Built as a hands-on practice project to strengthen the end-to-end data analysis workflow in Python.*
