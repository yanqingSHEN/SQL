### Question Link:[leetcode/Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)

## Solution
```sql
SELECT   
    COALESCE(
    (SELECT   DISTINCT Salary 
    FROM     Employee
    ORDER BY Salary DESC
    LIMIT 1 OFFSET 1),
    NULL    ) AS SecondHighestSalary
```

