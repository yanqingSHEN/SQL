### Quesion Link:[leetcode/Project Employees II](https://leetcode.com/problems/project-employees-ii/)


##  Solution 1 Subquery
```sql
SELECT   project_id
FROM     Project
GROUP BY project_id
HAVING   COUNT(*) = (SELECT MAX(num) FROM (
                                            SELECT   project_id,COUNT(*) AS num
                                            FROM     Project
                                            GROUP BY project_id) AS sub)
```


##  Solution 2  Windows Function (faster)
```sql
SELECT project_id
FROM   Project P
GROUP BY project_id
HAVING COUNT(*) = (SELECT MAX(num) FROM (SELECT COUNT(*) OVER(PARTITION BY project_id) AS num
                   FROM   Project) AS sub)
```                   
                   
## The following DOESN'T work
```sql
SELECT project_id
FROM   (
        SELECT project_id,COUNT(*) OVER(PARTITION BY project_id) AS num
        FROM   Project) AS sub
GROUP BY project_id
HAVING COUNT(*) = MAX(num)
```
In the outer query, the max(num) for each group(project) is exactly the num for that group. So this way doesn't output what we want.
