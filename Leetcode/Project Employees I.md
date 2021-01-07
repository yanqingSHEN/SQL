###  Question Link:[Leetcode/Project Employees I](https://leetcode.com/problems/project-employees-i/)


```sql
SELECT     project_id,round(cast(sum(E.experience_years) as decimal(10,2))/count(project_id),2) AS average_years 
FROM       Project P
INNER JOIN Employee E
ON         P.employee_id = E.employee_id
GROUP BY   project_id
ORDER BY   project_id
```
