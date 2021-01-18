###   Question Link:[ Leetcode/Monthly Transactions I](https://leetcode.com/problems/monthly-transactions-i/)


```sql
SELECT   DATE_FORMAT(trans_date, "%Y-%m") AS month,country,
         count(*) AS trans_count,
         count(CASE WHEN state = 'approved' THEN id END) AS approved_count,
         sum(amount) AS trans_total_amount,
         sum(CASE WHEN state = 'approved' THEN amount ELSE 0 END) AS approved_total_amount
FROM     Transactions
GROUP BY month,country
```
