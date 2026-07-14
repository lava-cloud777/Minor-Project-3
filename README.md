# RedFlag: SQL Fraud Detection Engine

An industry-graded analytics project detecting **12 complex fraud patterns** across 200,000 transaction records using **Pure MySQL**.

## 📌 Project Overview
As a Fraud Analyst at **PayFast** (a fictional Indian payment aggregator handling UPI, Card, Netbanking, and Wallet transactions), the objective was to analyze six months of raw transaction data (Jan–Jun 2024) and write targeted SQL queries to flag fraud signatures—without machine learning libraries or external scripts.

---

## 🔍 Fraud Patterns Detected

### Tier 1: Foundational Patterns
1. **Velocity Fraud**: Daily transaction bursts ($\ge 30$ txns/day).
2. **Round-Amount Clustering**: Unnatural concentration of exact round figures (100, 500, 1000, 5000, 10000).
3. **Card Testing**: Stolen card validation scripts hitting micro-purchases ($< \text{₹}10$).
4. **Failed-Then-Succeeded Pairs**: Persistent brute-force authorization attempts.
5. **Odd-Hour Concentration**: Accounts conducting $\ge 80\%$ of activity in the 2 AM–5 AM window.

### Tier 2: Subqueries & Advanced Aggregations
6. **Mule Accounts**: Fast cash-outs (Netbanking credit drained via UPI within 30 mins at $\ge 70\%$ value).
7. **Refund Abuse**: Exploitative chargeback rates ($> 40\%$ refund ratio on $\ge 20$ txns).
8. **Merchant Collusion**: Top 5 contributing users accounting for $>60\%$ of total merchant volume.
9. **Structuring (Smurfing)**: Deliberate evasion of regulatory KYC checks via exact ₹9,999.00 transactions.
10. **Dormant-Then-Active**: Account takeover signature marked by a $\ge 90$-day inactivity gap followed by burst usage.

### Tier 3: Advanced Analytical Window Functions
11. **Velocity Spike**: Peak monthly volume surging $\ge 5\times$ historical baseline monthly average.
12. **Geographic Impossibility**: Consecutive transactions occurring in different cities within $\le 60$ minutes.

---

## 🛠️ Tech Stack & SQL Concepts Used
* **Database**: MySQL 8.0
* **Aggregations & Filters**: `GROUP BY`, `HAVING`, `CASE WHEN`
* **Subqueries & Joins**: Correlated Subqueries, `EXISTS` clauses
* **Advanced Logic**: Common Table Expressions (CTEs)
* **Window Functions**: `LAG()`, `ROW_NUMBER()`, `SUM() OVER(PARTITION BY...)`
* **Datetime Operations**: `DATE()`, `HOUR()`, `DATE_FORMAT()`, `TIMESTAMPDIFF()`

---

## 🏃 Getting Started
1. Import the database schema and transactions table.
2. Run `RedFlag_YourName.sql` to execute the full detection script.
3. Verify suspect counts against flagged fraud rules.

