###  Question Link:[Leetcode/Unpopular Books](https://leetcode.com/problems/unpopular-books/)


```sql
SELECT      book_id,name
FROM        (
            SELECT      sub.book_id,name,
                        SUM (CASE WHEN dispatch_date BETWEEN '2018-06-23' AND '2019-06-23' 
                        THEN quantity ELSE 0 END) AS q
            FROM        (
                         SELECT      B.book_id,name
                         FROM        Books B
                         WHERE       available_from < '2019-05-23') AS sub1
            LEFT JOIN   Orders O
            ON          sub.book_id = O.book_id
            GROUP BY    sub.book_id,name) AS sub2
WHERE       q <10

```
