### Question Link: [leedcode/Trips and Users](https://leetcode.com/problems/trips-and-users/)

**Solution**
```sql
SELECT  Request_at AS 'Day',
        round(IFNULL(SUM(CASE WHEN LEFT(Status,9) = 'cancelled' THEN 1 ELSE 0 END)/COUNT(*),0),2) AS 'Cancellation Rate'
FROM      Trips
WHERE     Client_Id NOT IN (SELECT Users_Id FROM Users WHERE Banned='Yes') AND
          Driver_Id NOT IN (SELECT Users_Id FROM Users WHERE Banned='Yes') AND
          Request_at BETWEEN '2013-10-01' AND '2013-10-03'
GROUP BY  Request_at
