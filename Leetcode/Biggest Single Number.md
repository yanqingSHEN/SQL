### Question Link: [leetcode/Biggest Single Number](https://leetcode.com/problems/biggest-single-number/)

## Solution 1
```sql
SELECT   IFNULL(
                (SELECT   num
                 FROM     my_numbers
                 GROUP BY num
                 HAVING   count(num)=1
                 ORDER BY num DESC
                 LIMIT 1),NULL) AS num
```

## Solution 2
```sql
SELECT   max(num) AS num
FROM     (SELECT num
          FROM   my_numbers
          GROUP BY num
          HAVING   count(num)=1) AS sub
```


##  Return NULL when the result is empty
1. Use IFNULL which if the first argument is not NULL, the function returns the first argument. Otherwise, the second argument is returned.
2. Use subquery. When there is no such number in the subquery, the result will automatically return NULL.
