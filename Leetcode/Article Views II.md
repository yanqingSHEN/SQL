###   Question Link:[Leetcode/Article Views II](https://leetcode.com/problems/article-views-ii/)


```sql
SELECT      DISTINCT viewer_id AS id
FROM        (
SELECT      *,rank() OVER (PARTITION BY viewer_id,view_date ORDER BY article_id) AS num
FROM        Views) AS sub
WHERE       num > 1
ORDER BY    id
```
