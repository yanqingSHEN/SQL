### Question Link: [leetcode/Game Play Analysis II](https://leetcode.com/problems/game-play-analysis-ii/)

```sql
SELECT   A.player_id,device_id
FROM  (
SELECT   player_id,MIN(event_date) AS first_login
FROM     Activity
GROUP BY player_id) AS sub
INNER JOIN Activity AS A
ON         sub.player_id = A.player_id
WHERE      event_date = first_login
```
