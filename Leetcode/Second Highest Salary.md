### Question Link:[leetcode/Second Highest Salary](https://leetcode.com/problems/second-highest-salary/)

## Solution
```sql
SELECT   
    COALESCE(
    (SELECT   DISTINCT Salary 
    FROM     Employee
    ORDER BY Salary DESC
    LIMIT 1 OFFSET 1)) AS SecondHighestSalary
```

## Frequently used code

_COALSECE Function_

**COALESCE(val1, val2, ...., val_n)**
The COALESCE() function returns the first non-null value in a list.

We need COALESCE here because there may be null value for us to consider.
