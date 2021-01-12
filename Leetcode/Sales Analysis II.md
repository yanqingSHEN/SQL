###  Question Link:[Leetcode/Sales Analysis II](https://leetcode.com/problems/sales-analysis-ii/)


```sql
SELECT      buyer_id
FROM        (
SELECT      buyer_id,
            CASE WHEN product_name = 'S8' THEN 1 ELSE 0 END AS S8,
            CASE WHEN product_name = 'iPhone' THEN 1 ELSE 0 END AS ip
FROM        Product P
INNER JOIN  Sales   S
ON          P.product_id = S.product_id) as sub
GROUP BY    buyer_id
HAVING      sum(S8) > 0 AND sum(ip) =0
```
