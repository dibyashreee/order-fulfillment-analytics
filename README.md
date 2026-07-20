# Order Fulfillment Analytics — DataCo Supply Chain

An analysis of order fulfillment performance across a global supply chain, built on 180,519 real order records from the DataCo Smart Supply Chain dataset (January 2015 - September 2017).

The project combines exploratory data analysis, order management diagnostics, and demand forecasting in Python, delivered through an interactive Excel dashboard.

---

## Key Findings

**How reliably are orders delivered on time?**
Only 45.3% of orders ship on time company-wide. This rate has stayed flat for nearly three years, with no seasonal improvement - late delivery is the norm, not the exception.

**Does paying for faster shipping get you more reliable delivery?**
No. First Class shipments are late 100% of the time, Second Class 79.7%, and Standard Class 39.8%, while Same Day delivery is late 0% of the time. The delivery windows promised for premium shipping tiers appear set unrealistically tight against what operations can actually achieve.

**How many orders require manual intervention?**
10.8% of all orders are "problem orders" - canceled, flagged as fraud, placed on hold, or stuck in payment review - rather than flowing straight through to completion.

**Is the problem concentrated in one region or customer type?**
No. On-time delivery rate (44–46%) and problem order rate (9.9–11.1%) stay consistent across every region and every customer segment. This points to a company-wide process issue rather than a weak spot in a specific market or account type.

**Can future demand be forecasted reliably?**
Yes. A 6-month demand forecast for the three highest-volume categories (Cleats, Men's Footwear, Women's Apparel) achieved 6.7–7.5% forecast error - strong accuracy for a simple, interpretable model.

**So where should the business focus?**
Demand is already predictable; fulfillment is not. The clearest opportunity is closing the gap between what's promised to customers at checkout and what the fulfillment process can consistently deliver.

---

## Repository Structure
order-fulfillment-analytics/
│
├── README.md
├── requirements.txt
│
├── data/
│   └── DataCoSupplyChainDataset_sample.csv     #A 1,000-row sample of the full dataset
│
├── notebooks/
│   └── supply_chain_analysis.ipynb             #Full analysis: cleaning, KPIs, forecasting
│
├── dashboard/
│   └── SCM_KPI_Dashboard.xlsm                  #Interactive Excel dashboard with VBA
│
└── outputs/
    ├── monthly_kpis_summary.csv
    ├── monthly_problem_order_rate.csv
    ├── forecast_output.csv
    ├── mape_summary.csv
    └── *.png                                   #All exported charts

## Dataset

**Source:** [DataCo Smart Supply Chain for Big Data Analysis](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis) (Kaggle)

180,519 order records across 53 fields covering orders, shipping, customers, products, and profitability.

The full dataset is around 92MB and isn't included here. A 1,000-row random sample is provided in `data/` so anyone can see the structure of the data without downloading the full file.

---

## Approach

**Cleaning and preparing the data.** 
The dataset needed very little cleanup - almost no missing values and no duplicate records. From there, three fields were built to power everything downstream: shipping lead time, an on-time delivery flag, and a monthly time period.

**Looking at order health, not just shipping.**
Beyond whether orders arrived on time, the analysis looked at what happens to orders that don't complete normally - cancellations, fraud flags, holds, and payment reviews - and whether those issues cluster anywhere specific.

**Tracking performance over time.**
Monthly KPIs (on-time delivery rate, lead time, late delivery rate) were tracked by category to see how performance trends across nearly three years of data.

**Forecasting demand.** 
For the three best-selling categories, a time-series model (ARIMA) was used to forecast the next six months of demand, along with a confidence range and an accuracy check against actual historical values.

**Building an interactive dashboard.** The findings were brought together in an Excel dashboard with KPI cards that update based on a category filter, a forecast chart that switches between categories, and two automated tools: a one-click data refresh button and a macro that highlights underperforming months.

---

## Tools & Technologies

Python (Pandas, NumPy, Matplotlib, Statsmodels) · Jupyter Notebook · Excel (Power Query, Pivot Tables, VBA) · ARIMA Time-Series Forecasting

---
