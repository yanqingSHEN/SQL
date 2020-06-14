### Question Link: [Hackerrank/Symmetric Pairs](https://www.hackerrank.com/challenges/symmetric-pairs/problem)


## Solution 1
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

## Solution 2
```sql
WITH T1 AS(
SELECT      F1.X,F1.Y,COUNT(*) OVER (PARTITION BY F1.X,F1.Y) AS num
FROM        Functions AS F1
INNER JOIN  Functions AS F2
ON          F1.X=F2.Y AND F2.X=F1.Y
WHERE       F1.X<=F1.Y)
SELECT      DISTINCT(X),Y
FROM        T1
WHERE      (X!=Y) OR (X=Y AND num%2=0)
ORDER BY    X
```

## Logic
There are two scenarios: 1. X != Y, join two tables to find such pairs. 2. X = Y, appear at least twice to be considered symmetric.
