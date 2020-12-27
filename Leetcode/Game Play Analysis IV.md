### Game Play Analysis IV[leetcode/Game Play Analysis IV](https://leetcode.com/problems/game-play-analysis-iv/)

```sql
SELECT      ROUND(COUNT(*)/(SELECT COUNT(DISTINCT player_id) FROM Activity),2) AS fraction
FROM (
SELECT      player_id,MIN(event_date) AS first_login
FROM        Activity
GROUP BY    player_id) AS sub
INNER JOIN  Activity A1
ON          sub.player_id = A1.player_id AND first_login = event_date-1
```
