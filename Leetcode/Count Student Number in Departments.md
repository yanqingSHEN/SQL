###   Question Link:[Leetcode/Count Student Number in Departments](https://leetcode.com/problems/count-student-number-in-departments/)


```sql
SELECT    dept_name,COALESCE(num,0) AS student_number
FROM      department d
LEFT JOIN (
          SELECT    dept_id,COUNT(*) AS num
          FROM      student
          GROUP BY  dept_id) AS sub
          ON        d.dept_id = sub.dept_id
          ORDER BY  student_number DESC,dept_name
```
