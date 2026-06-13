# 🛍️ Retail Customer Behavior Analytics

<img width="1037" height="560" alt="image" src="https://github.com/user-attachments/assets/dccd1855-ca18-4f03-bded-5c04fcb56dcd" />



> **Analyzing 3,900 retail transactions to uncover purchasing trends, customer segments, and actionable marketing strategies — using Python, PostgreSQL, and Power BI.**

---

## 📌 Business Question

> *"How can the company leverage consumer shopping data to identify trends, improve customer engagement, and optimize marketing and product strategies?"*

---

## 📁 Project Structure

```
retail-customer-behavior-analytics/
│
├── data/
│   └── customer_shopping_behavior.csv       # Raw dataset (3,900 rows, 18 columns)
│
├── python/
│   └── Customer_Shopping_Behavior_Analysis.ipynb  # EDA, cleaning & feature engineering
│
├── sql/
│   └── business_queries.sql                 # 10 business analysis queries (PostgreSQL)
│
├── powerbi/
│   └── Customer_Behavior_Dashboard.pbix     # Interactive Power BI dashboard
│
├── presentation/
│   └── Customer_Shopping_Behavior_Analysis.pdf
│
└── README.md
```

---

## 🗂️ Dataset Overview

| Property | Detail |
|---|---|
| Rows | 3,900 |
| Columns | 18 |
| Missing Data | 37 nulls in `Review Rating` |
| Source | Simulated retail transaction data |

**Key features:** Customer ID, Age, Gender, Item Purchased, Category, Purchase Amount (USD), Location, Size, Color, Season, Review Rating, Subscription Status, Shipping Type, Discount Applied, Previous Purchases, Payment Method, Frequency of Purchases.

---

## 🐍 Step 1 — Python: Data Preparation & EDA

**Notebook:** `python/Customer_Shopping_Behavior_Analysis.ipynb`

### What was done:
- **Data Loading** — Imported dataset with `pandas`; inspected structure via `df.info()` and `.describe()`
- **Missing Data Handling** — Imputed 37 null values in `Review Rating` using the median rating per product category
- **Column Standardization** — Renamed all columns to `snake_case` for consistency
- **Feature Engineering:**
  - Created `age_group` column by binning customer ages into: Young Adult, Adult, Middle-aged, Senior
  - Derived `purchase_frequency_days` from purchase frequency labels
- **Redundancy Check** — Confirmed `discount_applied` and `promo_code_used` were redundant; dropped `promo_code_used`
- **Database Integration** — Connected to PostgreSQL via `psycopg2` / SQLAlchemy and loaded the clean DataFrame

### Key libraries:
```
pandas · numpy · matplotlib · seaborn · psycopg2 · sqlalchemy
```

---

## 🗄️ Step 2 — SQL: Business Analysis (PostgreSQL)

**File:** `sql/business_queries.sql`

Ten business queries were run against the cleaned dataset loaded into PostgreSQL:

| # | Query | Key Result |
|---|---|---|
| Q1 | Revenue by Gender | Male: $157,890 / Female: $75,191 |
| Q2 | High-Spending Discount Users | 839 customers spent above average while using discounts |
| Q3 | Top 5 Products by Rating | Gloves (3.86★), Sandals (3.84★), Boots (3.82★) |
| Q4 | Shipping Type Comparison | Express avg $60.48 vs Standard avg $58.46 |
| Q5 | Subscribers vs Non-Subscribers | Sub: $59.49 avg / Non-sub: $59.87 avg |
| Q6 | Discount-Dependent Products | Hat (50%), Sneakers (49.7%), Coat (49.1%) |
| Q7 | Customer Segmentation | Loyal: 3,116 · Returning: 701 · New: 83 |
| Q8 | Top 3 Products per Category | Clothing: Blouse, Pants, Shirt |
| Q9 | Repeat Buyers & Subscriptions | 958 repeat buyers subscribed vs 2,518 who didn't |
| Q10 | Revenue by Age Group | Young Adult leads at $62,143 |

---

## 📊 Step 3 — Power BI: Interactive Dashboard

**File:** `powerbi/Customer_Behavior_Dashboard.pbix`

The dashboard includes slicers for **Subscription Status**, **Gender**, **Category**, and **Shipping Type**, and visualizes:

- **KPI Cards** — Total Customers (3.9K), Avg Purchase ($59.76), Avg Rating (3.75★)
- **Donut Chart** — % Customers by Subscription Status (27% Yes / 73% No)
- **Bar Charts** — Revenue and Sales by Category
- **Horizontal Bar Charts** — Revenue and Sales by Age Group

---

## 💡 Key Insights

| # | Insight |
|---|---|
| 1 | **Gender Revenue Gap** — Male customers generate 2× more revenue, signaling under-leveraged potential in female-targeted marketing |
| 2 | **Strong Loyalty Base** — 80% of customers (3,116) are classified as Loyal — a prime audience for upselling and subscription conversion |
| 3 | **Subscription Opportunity** — Only 27% subscribe, yet average spend is nearly identical to non-subscribers. Subscriptions build retention at no revenue cost |
| 4 | **Discount Dependency Risk** — Hat, Sneakers, and Coat have ~50% discount rates, creating margin risk if discounts are needed to drive sales |
| 5 | **Young Adults Drive Revenue** — The 18–35 segment contributes $62,143 — the highest of all age groups |
| 6 | **Express Shipping Premium** — Express customers spend $2 more on average, indicating willingness to pay for convenience |

---

## ✅ Strategic Recommendations

### 🔴 High Priority
1. **Target the Female Segment** — Launch dedicated campaigns, category-specific promotions, and influencer partnerships to close the revenue gap
2. **Drive Subscription Conversions** — Convert the 73% non-subscribers with first-month incentives and loyalty perks (early access, exclusive deals)

### 🟡 Medium Priority
3. **Reduce Discount Dependency** — Phase out blanket discounts on high-dependency items (Hat, Sneakers, Coat); replace with a loyalty-points system
4. **Introduce a Premium Shipping Tier** — Bundle Express shipping with subscriptions; track NPS to measure the impact on satisfaction

---

## 🚀 Getting Started

### Prerequisites
```bash
pip install pandas numpy matplotlib seaborn sqlalchemy psycopg2-binary jupyter
```

### Run the Notebook
```bash
cd python
jupyter notebook Customer_Shopping_Behavior_Analysis.ipynb
```

### Load Data to PostgreSQL
The notebook includes a cell that connects to PostgreSQL and loads the cleaned DataFrame. Update the connection string in the notebook:
```python
engine = create_engine("postgresql://username:password@localhost:5432/your_database")
```

### Run SQL Queries
Open `sql/business_queries.sql` in pgAdmin, DBeaver, or any PostgreSQL client and run against the loaded table.

### Open the Dashboard
Open `powerbi/Customer_Behavior_Dashboard.pbix` in **Power BI Desktop** (free download from Microsoft).

---

## 🛠️ Tech Stack

| Tool | Purpose |
|---|---|
| Python (pandas, seaborn) | Data cleaning, EDA, feature engineering |
| PostgreSQL | Structured business queries |
| Power BI | Interactive dashboard & visualization |
| Jupyter Notebook | Analysis environment |

---

## 📄 License

This project is for educational and portfolio purposes.
