#  Olist E-Commerce SQL Analysis

---

##  Project Overview

This project analyzes **Olist**, a Brazilian e-commerce marketplace, using SQL to extract business insights from 4 relational datasets covering orders, products, payments, and customers.

> Dataset: 99,441 orders · 26 Brazilian states · Sep 2016 – Aug 2018

---

## Business Questions

| # | Business Question | 
|---|---|---|
| 1 | What is the overall marketplace health? | 
| 2 | How is revenue trending month over month? | 
| 3 | Who are our customers and where are they? |
| 4 | What is the customer repeat purchase rate? |
| 5 | Are we delivering on time? Where do we fail? |
| 6 | How do customers prefer to pay? | 
| 7 | Which sellers drive the most value? |
| 8 | What is the customer cohort retention rate? |

---

##  Dataset Schema

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

## Key Findings

###  Revenue
- Total revenue: **R$13.6M** over 2 years
- Peak month: **November 2017 (R$1.01M)** — Black Friday effect
- Revenue maintained **R$850K–R$1M/month** throughout 2018

###  Customers
- **96,096 unique customers** across 26 states
- São Paulo (SP) accounts for **41.97%** of all orders — high geographic concentration
- **78.6%** of customers made only 1 purchase — low retention, high acquisition opportunity

###  Delivery
- Average delivery time: **12.1 days** (median: 10 days)
- **91.9%** on-time delivery rate
- **8.1%** of orders (7,826) were delivered late

###  Payments
- **73.9%** of customers pay by credit card
- **50.5%** pay in full (1 installment)
- Boleto (bank slip) accounts for **19%** — significant unbanked customer base

---



Dataset source: [Olist Brazilian E-Commerce — Kaggle](https://www.kaggle.com/datasets/olistbr/brazilian-ecommerce)
