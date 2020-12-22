### Question Link:[leetcode/Highest Grade For Each Student](https://leetcode.com/problems/highest-grade-for-each-student/)

```sql
SELECT   student_id,course_id,grade
FROM     (
SELECT   student_id,course_id,grade,
         row_number() OVER (PARTITION BY E.student_id ORDER BY grade DESC,course_id) AS r
FROM     Enrollments E) AS sub
WHERE    r=1

```
