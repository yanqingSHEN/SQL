### Question Link:[leetcode/Exchange Seats](https://leetcode.com/problems/exchange-seats/)

```sql
SELECT   CASE WHEN (id%2!= 0 AND id < (SELECT MAX(id) FROM seat)) THEN id+1
              WHEN (id%2 = 0) THEN id-1
         ELSE id
         END AS id,student
FROM     seat
ORDER BY id
```
