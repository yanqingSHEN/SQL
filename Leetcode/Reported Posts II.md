###  Question Link:[Leetcode/Reported Posts II](https://leetcode.com/problems/reported-posts-ii/)


```sql
SELECT     ROUND(100*SUM(day_avg)/COUNT(action_date),2) AS average_daily_percent
FROM       (
            SELECT     action_date,
                       COUNT(DISTINCT R.post_id)/COUNT(DISTINCT A.post_id) AS day_avg
            FROM       Actions AS A
            LEFT JOIN  Removals AS R
            ON         A.post_id = R.post_id AND remove_date >= action_date
            WHERE      extra = 'spam'
            GROUP BY   action_date) AS sub
```


##  Notes:
Make sure to count distinct number of posts as one post can be reported by several users on the same day.
