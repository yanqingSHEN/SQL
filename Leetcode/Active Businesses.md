###  Question Link: [Leetcode/Active Businesses](https://leetcode.com/problems/active-businesses/)



##   Solution 1  Basic Join(faster than 90.41%)
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


##   Solution 2  Window Function(faster than 72.5%)
```sql
SELECT    business_id
FROM      (
           SELECT    *,AVG(occurences) OVER (PARTITION BY event_type) AS e_avg
           FROM      Events) AS sub
WHERE     occurences > e_avg
GROUP BY  business_id
HAVING    COUNT(distinct event_type) > 1
```
