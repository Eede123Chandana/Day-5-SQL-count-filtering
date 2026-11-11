# 📊 SQL COUNT() & Filtering | Day 5

## 🎯 Overview

The SQL `COUNT()` function and filtering operators are fundamental concepts used in data analytics and business intelligence.

They help measure data volume, identify unique records, filter transactions, and analyze business performance.

**Objective:** Understand COUNT() variations and SQL filtering operators with practical, real-world business examples.

---

## 1️⃣ What is COUNT()?

`COUNT()` is an aggregate function that returns the number of rows or non-NULL values matching a query.

### COUNT() Variations

| Function | Purpose |
|---|---|
| COUNT(*) | Counts all rows |
| COUNT(1) | Counts all rows |
| COUNT(column) | Counts non-NULL values |
| COUNT(DISTINCT column) | Counts unique non-NULL values |

### Sample Dataset

**Table: transactions**

| transaction_id | customer_id | amount | payment_method |
|---|---|---:|---|
| 101 | C001 | 2500 | UPI |
| 102 | C002 | 4500 | Card |
| 103 | C001 | 1200 | Cash |
| 104 | C003 | 6000 | UPI |
| 105 | NULL | 3000 | Card |

---

## 2️⃣ Understanding COUNT() Variations

### COUNT(*) – Total Records

```sql
SELECT COUNT(*) AS total_transactions
FROM transactions;
```

**Output:** 5

Counts all records, regardless of NULL values.

### COUNT(1) – Row Count

```sql
SELECT COUNT(1) AS total_transactions
FROM transactions;
```

**Output:** 5

Equivalent to COUNT(*) for counting rows.

### COUNT(column) – Non-NULL Values

```sql
SELECT COUNT(customer_id) AS customer_records
FROM transactions;
```

**Output:** 4

Excludes records where customer_id is NULL.

### COUNT(DISTINCT) – Unique Values

```sql
SELECT COUNT(DISTINCT customer_id)
AS unique_customers
FROM transactions;
```

**Output:** 3

Counts distinct customer IDs, excluding NULL values.

---

## 3️⃣ SQL Filtering Operators

Filtering allows us to retrieve specific records based on conditions.

| Operator | Description |
|---|---|
| WHERE | Filters rows based on conditions |
| AND | All conditions must be TRUE |
| OR | At least one condition must be TRUE |
| IN | Matches values in a list |
| NOT IN | Excludes values in a list |
| BETWEEN | Filters an inclusive range |

---

## 4️⃣ Filtering with WHERE

### Example: High-Value Transactions

```sql
SELECT *
FROM transactions
WHERE amount > 2000;
```

**Output:** 4 records

**Business Application:** Identify transactions exceeding a specified amount.

---

## 5️⃣ Logical Operators

### AND – Multiple Conditions

```sql
SELECT COUNT(*) AS upi_transactions
FROM transactions
WHERE amount > 2000
AND payment_method = 'UPI';
```

**Output:** 2

*Correction based on the sample data: the UPI transactions have amounts 2500 and 6000.*

### OR – Alternative Conditions

```sql
SELECT COUNT(*) AS digital_transactions
FROM transactions
WHERE payment_method = 'UPI'
OR payment_method = 'Card';
```

**Output:** 4

Identifies transactions using either payment method.

---

## 6️⃣ IN and NOT IN

### IN – Matching Multiple Values

```sql
SELECT COUNT(*) AS digital_payments
FROM transactions
WHERE payment_method IN ('UPI', 'Card');
```

**Output:** 4

**Use Case:** Analyze selected digital payment methods.

### NOT IN – Excluding Values

```sql
SELECT COUNT(*) AS other_payments
FROM transactions
WHERE payment_method NOT IN ('UPI', 'Card');
```

**Output:** 1

**Use Case:** Identify transactions using other payment methods.

**Important:** NULL values require special handling with NOT IN.

---

## 7️⃣ BETWEEN – Range Filtering

```sql
SELECT COUNT(*) AS transactions_in_range
FROM transactions
WHERE amount BETWEEN 1000 AND 5000;
```

**Output:** 4

BETWEEN includes both boundary values.

Equivalent condition:

```sql
WHERE amount >= 1000
AND amount <= 5000
```

**Business Application:** Identify transactions within a defined spending range.

---

## 8️⃣ Real-World Business Applications

### 🛒 Retail Analytics

**Objective:** Count total transactions.

```sql
SELECT COUNT(*) AS total_transactions
FROM transactions;
```

### 👥 Customer Analytics

**Objective:** Identify unique customers.

```sql
SELECT COUNT(DISTINCT customer_id)
AS unique_customers
FROM transactions;
```

### 🏬 Store Performance

**Objective:** Track transactions across different stores.

```sql
SELECT
    store_id,
    COUNT(*) AS transaction_count
FROM transactions
GROUP BY store_id;
```

*Requires a store_id column in the dataset.*

### 💳 Payment Method Trends

**Objective:** Analyze payment preferences.

```sql
SELECT
    payment_method,
    COUNT(*) AS transaction_count
FROM transactions
GROUP BY payment_method;
```

**Business Value:** Identify the most frequently used payment methods.

---

## 9️⃣ Important SQL Interview Questions

**Q1. COUNT(*) vs COUNT(column)?**

COUNT(*) counts all rows, while COUNT(column) counts only non-NULL values.

**Q2. COUNT(*) vs COUNT(1)?**

Both count rows because 1 is a non-NULL constant. Performance is generally similar.

**Q3. What does COUNT(DISTINCT) do?**

Counts unique, non-NULL values in a specified column.

**Q4. Does COUNT() include NULL values?**

COUNT(*) includes rows containing NULLs; COUNT(column) ignores NULL values in that column.

**Q5. Is BETWEEN inclusive?**

Yes, both lower and upper boundaries are included.

**Q6. What happens when no records match COUNT()?**

COUNT() returns 0.

---

## 🔟 Key Takeaways

✅ COUNT(*) measures total rows.

✅ COUNT(1) provides the same row count.

✅ COUNT(column) excludes NULL values.

✅ COUNT(DISTINCT) identifies unique values.

✅ WHERE filters records.

✅ AND and OR combine conditions.

✅ IN and NOT IN simplify multiple-value filtering.

✅ BETWEEN supports inclusive range filtering.

✅ COUNT() and filtering support KPI tracking and business reporting.

---

## 💡 Final Takeaway

**COUNT() tells us HOW MUCH data exists, while filtering identifies WHICH records matter.**

Together, these concepts help transform raw data into meaningful business insights, improve reporting, and support data-driven decisions.

### 🏷️ Topics

`SQL` `COUNT` `COUNT DISTINCT` `SQL Filtering` `WHERE` `AND` `OR` `IN` `NOT IN` `BETWEEN` `Data Analytics` `Business Intelligence` `MySQL`
