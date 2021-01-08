###  Question Link:[Leetcode/Sales Analysis I](https://leetcode.com/problems/sales-analysis-i/)


```sql
SELECT seller_id
FROM   Sales
GROUP BY seller_id
HAVING   sum(price) = (SELECT MAX(num) FROM (SELECT seller_id,SUM(price) AS num
                                             FROM   Sales
                                             GROUP BY seller_id) AS sub)
```
