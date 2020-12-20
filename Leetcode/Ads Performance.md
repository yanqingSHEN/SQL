### Question Link:[leetcode/Ads Performance](https://leetcode.com/problems/ads-performance/)

```sql
SELECT ad_id,IF(C+V=0,0,ROUND(C/(C+V)*100,2)) AS ctr
FROM   (
        SELECT ad_id,
               SUM(CASE WHEN action = 'Clicked' THEN 1 ELSE 0 END) AS C,
               SUM(CASE WHEN action = 'Viewed' THEN 1 ELSE 0 END) AS V
        FROM   Ads
        GROUP BY ad_id) AS sub
ORDER BY ctr DESC,ad_id
```
