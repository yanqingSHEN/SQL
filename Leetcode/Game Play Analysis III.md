### Question Link:[leetcode/Game Play Analysis III](https://leetcode.com/problems/game-play-analysis-iii/)

##  Solution 1 Window Function
```sql
SELECT player_id,event_date,
       SUM(games_played) OVER (PARTITION BY player_id ORDER BY event_date) AS games_played_so_far
FROM   Activity
```

##  Solution 2 Join
```sql
SELECT     A1.player_id,A1.event_date,
           A1.games_played+SUM(COALESCE(A2.games_played,0)) AS games_played_so_far
FROM       Activity A1
LEFT JOIN  Activity A2
ON         A1.player_id = A2.player_id AND A1.event_date > A2.event_date
GROUP BY   A1.player_id,A1.event_date
ORDER BY   A1.event_date
```

## Notes for Solution 2
1. Use left join to keep the first login date for each player
2. As the first login date is the earliest date, there is null in the second table for those records. Use coalesce to ensure correct result for those dates
3. The rolling sum = the number of games played on the date + the number of games played prior to the date

