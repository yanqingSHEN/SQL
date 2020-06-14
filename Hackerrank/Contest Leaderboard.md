### Question Link: [Hackerrank/Contest Leaderboard](https://www.hackerrank.com/challenges/contest-leaderboard/problem)


## Solution 1
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


## Solution 2
```sql
WITH T1 AS(
SELECT Hackers.hacker_id,name,score,
       row_number() over (partition by Hackers.hacker_id,challenge_id order by score DESC) as max_score
FROM   Hackers
INNER JOIN Submissions
ON     Hackers.hacker_id = Submissions.hacker_id)
SELECT hacker_id,name,sum(score) AS sum_score 
FROM   T1
WHERE  max_score=1
GROUP BY hacker_id,name 
HAVING sum(score) != 0
ORDER BY sum_score DESC,hacker_id

## Logic
First find the maximum score for each challenge of everyone, and then sum the max score. Finally join with the other table to get names.
