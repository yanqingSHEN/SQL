###  Question Link: [Leetcode/Active Businesses](https://leetcode.com/problems/active-businesses/)


```sql
SELECT   business_id
FROM     Events AS E
INNER JOIN (
            SELECT   event_type,SUM(occurences)/COUNT(business_id) AS e_avg
            FROM     Events
            GROUP BY event_type) AS sub
ON        E.event_type = sub.event_type
GROUP BY  business_id
HAVING    sum(occurences > e_avg) >= 2
```
