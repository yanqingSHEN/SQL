###   Question Link:[Leetcode/Sales Analysis III](https://leetcode.com/problems/sales-analysis-iii/)


```sql
SELECT      product_id,product_name
FROM        (
SELECT      S.product_id,product_name,
            CASE WHEN sale_date < '2019-01-01' or sale_date >'2019-03-31' THEN 1
            ELSE 0
            END AS test
FROM        Product P
INNER JOIN  Sales   S
ON          P.product_id = S.product_id) AS sub 
GROUP BY    product_id,product_name
HAVING      sum(test) = 0
```
