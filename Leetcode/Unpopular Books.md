###  Question Link:[Leetcode/Unpopular Books](https://leetcode.com/problems/unpopular-books/)


```sql
SELECT      sub.book_id,name
FROM        (
             SELECT      B.book_id,name
             FROM        Books B
             WHERE       available_from < '2019-05-23') AS sub
LEFT JOIN   Orders O
ON          sub.book_id = O.book_id AND 
            dispatch_date BETWEEN '2018-06-23' AND '2019-06-23'
GROUP BY    sub.book_id,name
HAVING      SUM(IFNULL(quantity,0)) < 10
```


##   Learning
1. Use LEFT JOIN to make sure all books that are available longer than 1 month are included
2. User IFNULL to replace the null value of books that don't have sales in the past year
