### Question Link: [Hackerrank/Challenges](https://www.hackerrank.com/challenges/challenges/problem)

##  Solution 

```sql
SELECT H.hacker_id,H.name,count(challenge_id) as nu
FROM   Hackers AS H
INNER JOIN Challenges AS C
ON     H.hacker_id = C.hacker_id
Group by H.hacker_id,H.name
HAVING nu = (SELECT MAX(Sub1.nu1) FROM (SELECT H1.hacker_id,count(challenge_id) as nu1
                                        FROM   Hackers AS H1
                                        INNER JOIN Challenges AS C1
                                        ON     H1.hacker_id = C1.hacker_id
                                        Group by H1.hacker_id) AS Sub1) OR
       nu IN (SELECT Sub2.nu2 FROM (SELECT H2.hacker_id,count(challenge_id) as nu2
                                    FROM   Hackers AS H2
                                    INNER JOIN Challenges AS C2
                                    ON     H2.hacker_id = C2.hacker_id
                                    Group by H2.hacker_id) AS Sub2 
                                    GROUP BY nu2 HAVING count(nu2)=1)
ORDER BY nu DESC,H.hacker_id
```

##  Logic 
This question looks complicated at the first glance.The basic query used finds out how many challenges each hacker solved. Then the question asks us to get hacker's information 
if he/she satisfies either of the following criteria: 1) the person is among the hackers who solve the maximum number of challenges 2) the number of challenges the person solved is
unique. Having clause helps us to build up the above two criteria. 
