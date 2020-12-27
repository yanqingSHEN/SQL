### Question Link:[leetcode/Exchange Seats](https://leetcode.com/problems/exchange-seats/)

```sql
SELECT   CASE WHEN (id%2!= 0 AND id < (SELECT MAX(id) FROM seat)) THEN id+1
              WHEN (id%2 = 0) THEN id-1
         ELSE id
         END AS id,student
FROM     seat
ORDER BY id
```


## Three senarios:
1. The student has an odd id and isn't the last one: id = id+1
2. The student has an even id: id = id-1
3. The student has an odd id and is the last one: id remains the same
