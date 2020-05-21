### Question Link: [Hackerrank/Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem)


## Solution
```sql
WITH T1 AS(
SELECT   hacker_id,challenge_id,MAX(score) AS s
FROM     Submissions
GROUP BY hacker_id,challenge_id
),
T2 AS(
SELECT   T1.hacker_id,SUM(s) AS tol_score
FROM     T1
GROUP BY T1.hacker_id)
SELECT   T2.hacker_id,name,tol_score
FROM     T2
INNER JOIN Hackers
ON       T2.hacker_id = Hackers.hacker_id
WHERE    tol_score !=0
ORDER BY tol_score DESC,T2.hacker_id
```

## Logic
First find the maximum score for each challenge of everyone, and then sum the max score. Finally join with the other table to get names.
