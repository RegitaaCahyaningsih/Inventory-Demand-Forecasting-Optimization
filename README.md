# 📦 Inventory Demand Forecasting & Optimization
End-to-end data science project for SKU-level demand forecasting and inventory optimization, using machine learning and business-driven inventory logic.
This project simulates a real retail/FMCG inventory portfolio, covering forecasting, reorder decisions, SKU prioritization, and executive-level insights.

**🚀 Project Overview**

Retail inventory decisions are often driven by intuition, leading to:
- Overstock (dead stock)
- Stock-out (lost sales)
- Inefficient cash allocation

This project solves that problem by:
- Forecasting daily demand per SKU
- Calculating optimal reorder points
- Ranking SKU restock urgency
- Classifying fast / slow / dead stock
- Producing executive-ready insights & dashboards

**🧠 Business Questions Answered**

- Which SKUs must be reordered urgently?
- How much stock should be reordered per SKU?
- Which products are fast-moving vs dead stock?
- How can procurement focus budget on high-impact SKUs?
- What is the overall inventory health of the portfolio?

**🗂️ Project Structure**

inventory-forecasting/
│
├── data/
│   ├── raw/
│   │   └── Data Stock Sample.xlsx
│   └── output/
│       └── inventory_optimization_output.xlsx
│
├── src/
│   ├── preprocess.py        # Data cleaning & formatting
│   ├── features.py          # Time-series feature engineering
│   ├── model.py             # ML model (XGBoost)
│   ├── forecast.py          # 30-day demand forecasting
│   ├── inventory.py         # Inventory optimization logic
│   └── visualization.py     # Forecast & inventory plots
│
├── notebooks/
│   └── inventory_analysis.ipynb
│
├── run_forecast.py          # Main pipeline runner
├── README.md
└── requirements.txt

**📊 Dataset Description**

Each record represents daily sales per SKU.

Key columns:

- date – transaction date
- sku – product code
- product_name – product name
- units_sold – daily sales
- stock_on_hand – current inventory-
- last_price, last_cost – pricing info

Dummy data simulates:

- 200+ SKUs
- Random appearance dates
- Realistic retail demand patterns

**🔧 Feature Engineering**

Time-series features:

- Day of week
- Month
- Lag demand (1, 7, 14 days)
- Rolling averages (7, 14 days)

These features capture:

- Seasonality
- Short-term demand momentum
- Sales stability

**Machine Learning Model**

- Model: XGBoost Regressor
- Target: Daily units sold
- Forecast Horizon: 30 days per SKU
- Training: Walk-forward split (no shuffling)

**📦 Inventory Optimization Logic**

Inventory decisions are based on:

- Average daily demand
- Lead time (default: 3 days)
- Service level (default: 95%)

Key outputs:

- avg_daily_demand
- reorder_point
- restock_needed
