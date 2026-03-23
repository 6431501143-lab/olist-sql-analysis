#  Olist E-Commerce SQL Analysis

---

##  Project Overview

This project analyzes **Olist**, a Brazilian e-commerce marketplace, using SQL to extract business insights from 4 relational datasets covering orders, products, payments, and customers.

The analysis covers **99,441 orders** across **26 Brazilian states** from **September 2016 to August 2018**, generating actionable insights on sales trends, customer behavior, delivery performance, and seller effectiveness.

---

## 🎯 Business Questions Answered

| # | Business Question | SQL Techniques Used |
|---|---|---|
| 1 | What is the overall marketplace health? | Aggregation, JOINs |
| 2 | How is revenue trending month over month? | DATE_TRUNC, LAG, Window Functions |
| 3 | Who are our customers and where are they? | GROUP BY, CTEs |
| 4 | What is the customer repeat purchase rate? | CTEs, Subqueries |
| 5 | Are we delivering on time? Where do we fail? | PERCENTILE_CONT, CASE WHEN |
| 6 | How do customers prefer to pay? | Aggregation, Window Functions |
| 7 | Which sellers drive the most value? | RANK(), PARTITION BY |
| 8 | What is the customer cohort retention rate? | Cohort Analysis, CTEs |

---

## 📁 Dataset Schema

```
customers          orders             order_items        order_payments
─────────────      ──────────────     ───────────────    ──────────────────
customer_id    ←── customer_id        order_id       ──→ order_id
customer_         order_id        ──→ order_item_id      payment_sequential
unique_id         order_status        product_id          payment_type
customer_city     purchase_ts         seller_id           payment_installments
customer_state    approved_at         price               payment_value
                  delivered_date      freight_value
                  estimated_date
```

---

## 🔍 Key Findings

### 💰 Revenue
- Total revenue: **R$13.6M** over 2 years
- Peak month: **November 2017 (R$1.01M)** — Black Friday effect
- Revenue maintained **R$850K–R$1M/month** throughout 2018

### 👥 Customers
- **96,096 unique customers** across 26 states
- São Paulo (SP) accounts for **41.97%** of all orders — high geographic concentration
- **78.6%** of customers made only 1 purchase — low retention, high acquisition opportunity

### 🚚 Delivery
- Average delivery time: **12.1 days** (median: 10 days)
- **91.9%** on-time delivery rate
- **8.1%** of orders (7,826) were delivered late

### 💳 Payments
- **73.9%** of customers pay by credit card
- **50.5%** pay in full (1 installment)
- Boleto (bank slip) accounts for **19%** — significant unbanked customer base

---

## 📊 SQL Techniques Demonstrated

```sql
-- Window Functions
LAG(), LEAD(), RANK(), DENSE_RANK(), NTILE()
SUM() OVER(), AVG() OVER()
FIRST_VALUE(), LAST_VALUE()
ROWS BETWEEN ... AND ...

-- Aggregate Functions
PERCENTILE_CONT(), COUNT(DISTINCT), ROUND()

-- CTEs & Subqueries
WITH ... AS (), nested subqueries, multi-step CTEs

-- Date Functions
DATE_TRUNC(), EXTRACT(), AGE()

-- Conditional Logic
CASE WHEN, NULLIF(), COALESCE()

-- Views
CREATE OR REPLACE VIEW for reusable BI-ready queries
```

---

## 🗂️ Project Structure

```
olist-sql-analysis/
│
├── olist_sql_project.sql        # All SQL queries (8 sections)
├── README.md                    # This file
│
├── data/
│   ├── olist_orders_dataset.csv
│   ├── olist_order_items_dataset.csv
│   ├── olist_order_payments_dataset.csv
│   └── olist_customers_dataset.csv
│
└── insights/
    └── olist_insights_report.pdf   # Business insights summary
```

---

## 🚀 How to Run

### Option A: PostgreSQL
```bash
# 1. Create database
createdb olist_db

# 2. Connect and run
psql -d olist_db -f olist_sql_project.sql

# 3. Import CSV data
\COPY customers FROM 'data/olist_customers_dataset.csv' CSV HEADER;
\COPY orders FROM 'data/olist_orders_dataset.csv' CSV HEADER;
\COPY order_items FROM 'data/olist_order_items_dataset.csv' CSV HEADER;
\COPY order_payments FROM 'data/olist_order_payments_dataset.csv' CSV HEADER;
```

### Option B: SQLite / DBeaver / DataGrip
Import CSV files directly into tables, then run each section of the `.sql` file.

---

## 💡 Business Recommendations

1. **Expand beyond São Paulo** — 3 states drive 66% of revenue; regional marketing campaigns could unlock growth
2. **Address late deliveries** — 8.1% late rate, focus on high-delay states for logistics improvement
3. **Bundle/Upsell strategy** — 78.6% of orders contain only 1 item; product recommendations can raise AOV
4. **Flash sales at peak hours** — Orders peak 10:00–21:00 with highest volume at 16:00
5. **Improve customer retention** — Most customers buy only once; loyalty programs could dramatically increase LTV

---

## 👤 About

**Portfolio project** showcasing SQL skills for Data Analyst / Business Analyst internship applications.

Dataset source: [Olist Brazilian E-Commerce — Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
