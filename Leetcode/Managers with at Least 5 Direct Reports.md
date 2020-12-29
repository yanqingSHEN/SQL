###  Question Link:[Leetcode/Managers with at Least 5 Direct Reports](https://leetcode.com/problems/managers-with-at-least-5-direct-reports/)


##   Solution 1 In clause
```sql
SELECT   Name
FROM     Employee
WHERE    Id IN (
                SELECT   ManagerId
                FROM     Employee
                GROUP BY ManagerID
                HAVING   COUNT(*) >=5)
```

##   Solution 2 Join two tables
```sql
SELECT     Name
FROM       Employee E
INNER JOIN
           (SELECT   ManagerId
           FROM     Employee
           GROUP BY ManagerID
           HAVING   COUNT(*) >=5) AS sub
ON         E.Id = sub.ManagerId


##   Solution 3 Join two tables & Window Function
```sql
SELECT   DISTINCT Name
FROM     Employee E
INNER JOIN (
            SELECT   ManagerId,COUNT(*) OVER (PARTITION BY ManagerId) AS num
            FROM     Employee) AS sub
            ON       E.Id = sub.ManagerId
            WHERE    num >=5
```
