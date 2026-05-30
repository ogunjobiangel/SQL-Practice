# 🗄️ SQL Practice — Banking & Finance Datasets

**Author:** Angel Ogunjobi | [@ogunjobiangel](https://github.com/ogunjobiangel)  
**Tools:** SQL (MySQL / PostgreSQL) | Banking Datasets | Data Querying

---

## About This Repository

This repository contains SQL queries and exercises focused on banking and financial datasets. It demonstrates my ability to extract, filter, aggregate, and analyse data from relational databases — a core skill in banking analytics and business intelligence roles.

---

## Repository Structure

```
SQL-Practice/
│
├── 01_basic_queries/
│   ├── select_and_filter.sql
│   ├── sorting_and_limiting.sql
│   └── string_functions.sql
│
├── 02_aggregations/
│   ├── group_by_analysis.sql
│   ├── having_clauses.sql
│   └── count_sum_avg.sql
│
├── 03_banking_exercises/
│   ├── customer_segmentation.sql
│   ├── transaction_analysis.sql
│   ├── loan_default_query.sql
│   └── monthly_balance_trends.sql
│
└── 04_joins_and_subqueries/
    ├── inner_outer_joins.sql
    └── subquery_examples.sql
```

---

## Sample Queries

### 🔍 Top 10 Customers by Transaction Volume
```sql
SELECT 
    customer_id,
    customer_name,
    COUNT(transaction_id) AS total_transactions,
    SUM(amount) AS total_amount
FROM transactions
WHERE transaction_date >= '2024-01-01'
GROUP BY customer_id, customer_name
ORDER BY total_transactions DESC
LIMIT 10;
```

### 🏦 Monthly Deposit vs Withdrawal Summary
```sql
SELECT 
    DATE_FORMAT(transaction_date, '%Y-%m') AS month,
    SUM(CASE WHEN type = 'deposit' THEN amount ELSE 0 END) AS total_deposits,
    SUM(CASE WHEN type = 'withdrawal' THEN amount ELSE 0 END) AS total_withdrawals,
    SUM(CASE WHEN type = 'deposit' THEN amount ELSE 0 END) - 
    SUM(CASE WHEN type = 'withdrawal' THEN amount ELSE 0 END) AS net_flow
FROM transactions
GROUP BY month
ORDER BY month;
```

### ⚠️ Flagging High-Risk Loan Accounts
```sql
SELECT 
    account_id,
    customer_name,
    loan_amount,
    outstanding_balance,
    ROUND((outstanding_balance / loan_amount) * 100, 2) AS repayment_rate_pct
FROM loans
WHERE outstanding_balance / loan_amount > 0.70
ORDER BY outstanding_balance DESC;
```

---

## Skills Demonstrated
- SELECT, WHERE, ORDER BY, LIMIT
- GROUP BY, HAVING, aggregate functions (COUNT, SUM, AVG, MIN, MAX)
- JOINs (INNER, LEFT, RIGHT)
- Subqueries and nested queries
- CASE WHEN conditional logic
- Date functions and filtering
- Banking-specific query patterns (transactions, loans, customer data)

---

*Part of my data analytics portfolio | [View full GitHub profile](https://github.com/ogunjobiangel)*

