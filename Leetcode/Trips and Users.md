### Question Link: [leedcode/Trips and Users](https://leetcode.com/problems/trips-and-users/)

**Solution**
```sql
SELECT    Request_at AS 'Day',
          round(IFNULL(SUM(CASE WHEN LEFT(Status,9) = 'cancelled' THEN 1 ELSE 0 END)/COUNT(*),0),2) AS 'Cancellation Rate'
FROM      Trips
WHERE     Client_Id IN (SELECT Users_Id FROM Users WHERE Banned='No') AND
          Driver_Id IN (SELECT Users_Id FROM Users WHERE Banned='No') AND
          Request_at BETWEEN '2013-10-01' AND '2013-10-03'
GROUP BY  Request_at

*******Frequently used code******
_LEFT function_
LEFT(string, number_of_chars) 
Extract 3 characters from a string (starting from left)
Here left function assigns value to 'cancelled trip' in an easy way.

*IFNULL function*
IFNULL(expression, alt_value)
The IFNULL() function returns a specified value if the expression is NULL.
