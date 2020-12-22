### Question Link:[leetcode/Find the Team Size](https://leetcode.com/problems/find-the-team-size/)

## Solution 1
```sql
SELECT employee_id,num AS team_size
FROM(
SELECT team_id,count(*) AS num
FROM   Employee E1
GROUP BY team_id) AS sub
INNER JOIN Employee E2
ON     sub.team_id = E2.team_id
```

## Solution 2
```sql
SELECT employee_id,num AS team_size
FROM(
SELECT *,COUNT(*) OVER (PARTITION BY team_id) AS num
FROM   Employee) AS sub
```
