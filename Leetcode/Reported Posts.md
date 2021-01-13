### Question Link:[Leetcode/Reported Posts](https://leetcode.com/problems/reported-posts/)



```sql
SELECT  extra AS report_reason, COUNT(DISTINCT post_id) AS report_count
FROM    Actions
WHERE   action_date = '2019-07-05' - INTERVAL 1 DAY AND extra IS NOT NULL
GROUP BY extra
HAVING   SUM(action = 'report')!=0
```
