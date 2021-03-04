### Question Link:[Leetcode/Report Contiguous Dates](https://leetcode.com/problems/report-contiguous-dates/)

```sql
SELECT      'failed' AS period_state,
            MIN(fail_date) AS start_date,MAX(fail_date) AS end_date
FROM       (
SELECT     fail_date,
           fail_date-INTERVAL (ROW_NUMBER() OVER (ORDER BY fail_date)) DAY AS diff
FROM       Failed
WHERE      fail_date BETWEEN '2019-01-01' AND '2019-12-31') AS sub1
GROUP BY   diff
UNION ALL
SELECT      'succeeded' AS period_state,
            MIN(success_date) AS start_date,MAX(success_date) AS end_date
FROM       (
SELECT     success_date,
           success_date-INTERVAL (ROW_NUMBER() OVER (ORDER BY success_date)) DAY AS diff
FROM       Succeeded
WHERE      success_date BETWEEN '2019-01-01' AND '2019-12-31') AS sub2
GROUP BY   diff
ORDER BY   start_date
```
