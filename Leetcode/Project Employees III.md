###  Question Link:[Leetcode/Project Employees III](https://leetcode.com/problems/project-employees-iii/)


```sql
SELECT     P2.project_id,P2.employee_id
FROM       Project P2
INNER JOIN Employee E2
ON         P2.employee_id = E2.employee_id
INNER JOIN (
SELECT     project_id,MAX(experience_years) as experienced
FROM       Project P1
INNER JOIN Employee E1
ON         P1.employee_id = E1.employee_id
GROUP BY   project_id) AS sub
ON         P2.project_id = sub.project_id AND E2.experience_years = experienced
```
