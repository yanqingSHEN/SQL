### Question Link: [Hackerrank/Symmetric Pairs](https://www.hackerrank.com/challenges/symmetric-pairs/problem)


## Solution
```sql
SELECT  F1.X,F1.Y
FROM    Functions AS F1
WHERE   F1.X = F1.Y
GROUP BY F1.X,F1.Y
HAVING COUNT(*)>1
UNION ALL
SELECT  F2.X,F2.Y
FROM    Functions AS F2
INNER JOIN Functions AS F3
WHERE   F2.X = F3.Y AND F2.Y = F3.X AND F2.X < F2.Y
ORDER BY X
```

## Logic
There are two scenarios: 1. X != Y, join two tables to find such pairs. 2. X = Y, appear at least twice to be considered symmetric.
