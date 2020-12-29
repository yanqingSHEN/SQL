### Question Link:[leetcode/Product Price at a Given Date](https://leetcode.com/problems/product-price-at-a-given-date/)

```sql
SELECT  product_id,10 AS price
FROM    Products
WHERE   product_id NOT IN (
                           SELECT product_id
                           FROM   Products
                           WHERE  change_date <= '2019-08-16')
union  
SELECT  product_id,new_price AS price
FROM    (
         SELECT *, 
                ROW_NUMBER() OVER (PARTITION BY product_id ORDER BY change_date DESC) AS num
         FROM   Products
         WHERE  change_date <= '2019-08-16') AS sub
WHERE    num = 1
```
