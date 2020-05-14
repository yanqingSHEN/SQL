### Question Link: [Hackerrank/The Report](https://www.hackerrank.com/challenges/the-report/problem)


## Solution
```sql

SELECT CASE WHEN Grade >=8 THEN Name
       ELSE NULL END AS N,
       Grade,Marks
FROM(
SELECT ID,Name,Marks, Grade
FROM   Students,Grades
WHERE  Marks BETWEEN Min_Mark AND Max_Mark
) AS SubQ
ORDER BY Grade DESC,N,Marks
```

## Frequently Used Code

_Between Function_


**WHERE column_name BETWEEN value1 AND value2**

selects values within a given range
