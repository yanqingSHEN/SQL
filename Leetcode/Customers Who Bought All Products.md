### Question Link:[leetcode/Customers Who Bought All Products](https://leetcode.com/problems/customers-who-bought-all-products/)

```sql
SELECT     customer_id
FROM       Customer C
GROUP BY   customer_id
HAVING     COUNT(DISTINCT(product_key)) = (SELECT COUNT(*) FROM Product)
```


Note that one customer could buy a particular product several times
