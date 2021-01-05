###   Qustion Link:[Leetcode/Median Employee Salary](https://leetcode.com/problems/median-employee-salary/)


```sql
SELECT   Id,Company,Salary
FROM (
      SELECT   *,ROW_NUMBER() OVER (PARTITION BY Company ORDER BY Salary) as r,
               COUNT(*) OVER (PARTITION BY Company) as num
      FROM     Employee) AS sub
WHERE    ((num%2=0) AND (r=num/2 or r=num/2+1)) OR (num%2 !=0 AND r=(num+1)/2)
ORDER BY Company,Salary
```
