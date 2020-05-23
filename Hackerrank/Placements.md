### Question Link: [Hackerrank/Placements](https://www.hackerrank.com/challenges/placements/problem)


## Solution
```sql
SELECT Students.Name
FROM(SELECT F1.ID,P1.Salary AS own,P2.Salary AS friend
     FROM   Friends AS F1
     INNER JOIN Packages As P1
     ON     F1.ID = P1.ID
     INNER JOIN Packages AS P2
     ON     F1.Friend_ID = P2.ID) AS SubQ
INNER JOIN Students
ON     SubQ.ID = Students.ID
WHERE  friend > own
Order by friend 
```

## Logic
Use subquery to put own & friend's salary to the same table, and then join the Students table to find the names.
