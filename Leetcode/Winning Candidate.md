### Question Link:[leetcode/Winning Candidate](https://leetcode.com/problems/winning-candidate/)

```sql
SELECT  Name
FROM    Candidate
WHERE   id = (
              SELECT   CandidateId
              FROM     Vote
              GROUP BY CandidateId
              ORDER BY COUNT(*) DESC
              LIMIT 1)
```

