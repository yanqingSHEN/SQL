###   Question Link：[Leetcode/Sales Person](https://leetcode.com/problems/sales-person/)


```sql
SELECT    name
FROM      salesperson 
WHERE     sales_id  NOT IN(
                            SELECT    o.sales_id
                            FROM      salesperson  s
                            LEFT JOIN orders       o
                            ON        s.sales_id = o.sales_id
                            INNER JOIN company     c
                            ON        c.com_id = o.com_id
                            WHERE     c.name = 'RED')
```
