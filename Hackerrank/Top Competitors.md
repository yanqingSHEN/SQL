### Question Link: [Hackerrank/Top Competitors](https://www.hackerrank.com/challenges/full-score/problem)


## Solution
```sql

SELECT H.hacker_id,H.name
FROM   Hackers AS H
INNER JOIN Submissions AS S
ON     H.hacker_id = S.hacker_id 
INNER JOIN Challenges AS C
ON     S.challenge_id = C.challenge_id
INNER JOIN  Difficulty AS D
ON     C.difficulty_level = D.difficulty_level
WHERE  S.Score=D.score AND C.difficulty_level = D.difficulty_level
GROUP BY H.hacker_id,H.name
HAVING count(H.hacker_id)>1
order by count(H.hacker_id) desc, H.hacker_id asc
```


## HAVING clause
1. the order of processing:
   First, WHERE filters **records** Next, GROUP BY takes all remaining records and forms groups. Finally, HAVING filters **groups**
 
2. Will always use **aggregate functions** to filter groups using the HAVING clause

3. DifferenTfrom GROUP BY: Aggregate functions in the HAVING clause are not required to be included in the SELECT command

