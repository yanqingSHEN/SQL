### Question Link: [leetcode/Customers Who Bought Products A and B but Not C](https://leetcode.com/problems/customers-who-bought-products-a-and-b-but-not-c/)

##  Solution
```sql
SELECT      customer_id,customer_name
FROM(
SELECT      Customers.customer_id,customer_name,
            CASE WHEN product_name = 'A' or product_name = 'B' THEN 1
            ELSE 0
            END AS    test_AB,
            CASE WHEN product_name = 'C' THEN 1
            ELSE 0
            END AS    test_C
FROM        Customers
INNER JOIN  Orders
ON          Customers.customer_id = Orders.customer_id) AS SubQ
GROUP BY    customer_id,customer_name
HAVING      sum(test_AB) = 2 AND sum(test_C) = 0
```
