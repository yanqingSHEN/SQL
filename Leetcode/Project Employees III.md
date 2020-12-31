###  Question Link:[Leetcode/Project Employees III](https://leetcode.com/problems/project-employees-iii/)


##   Solution 1  Subquery
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

##  Solution 2  Window Function
```sql
SELECT      project_id,employee_id
FROM        (
SELECT      p.project_id,p.employee_id,
            rank() OVER (PARTITION BY project_id ORDER BY experience_years DESC) AS r
FROM        Project  P
INNER JOIN  Employee E
ON          P.employee_id = E.employee_id) AS sub
WHERE       r=1
```
