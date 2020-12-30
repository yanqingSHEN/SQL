### Question Link: [leetcode/Customers Who Bought Products A and B but Not C](https://leetcode.com/problems/customers-who-bought-products-a-and-b-but-not-c/)

##  Solution
```sql
SELECT   customer_id,customer_name
FROM  (
SELECT   C.customer_id,customer_name,
         CASE WHEN product_name = 'A' THEN 1 ELSE 0 END AS check_A,
         CASE WHEN product_name = 'B' THEN 1 ELSE 0 END AS check_B,
         CASE WHEN product_name = 'C' THEN 1 ELSE 0 END AS check_C
FROM     Orders O
INNER JOIN Customers C
ON       O.customer_id = C.customer_id) AS sub
GROUP BY customer_id,customer_name
HAVING   sum(check_A) != 0 AND sum(check_B) !=0 AND sum(check_C)=0
```
