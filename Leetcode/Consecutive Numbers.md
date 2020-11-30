### Question Link: [leetcode/Consecutive Numbers](https://leetcode.com/problems/consecutive-numbers/)

##  Solution 1
```sql
SELECT      DISTINCT (L1.Num)  AS ConsecutiveNums
FROM        Logs AS L1
INNER JOIN  Logs AS L2
ON          L1.Id = L2.Id-1
INNER JOIN  Logs AS L3
ON          L2.Id = L3.Id-1
WHERE       L1.Num = L2.Num AND L1.Num = L3.Num
```

##  Solution 2 (Window Function)
```sql
SELECT  DISTINCT Num AS ConsecutiveNums
FROM    (
SELECT  Num,Lead(Num,1) OVER (ORDER BY Id) AS oa,Lead(Num,2) OVER (ORDER BY Id) AS ta
FROM    Logs) AS T1
WHERE   Num = oa AND oa = ta
```

##  Frequently used code

_Distinct Function_


The SELECT DISTINCT statement is used to return only distinct (different) values.
