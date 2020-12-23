### Question Link:[leetcode/Highest Grade For Each Student](https://leetcode.com/problems/highest-grade-for-each-student/)

## Solution 1 Window Function
```sql
SELECT   student_id,course_id,grade
FROM     (
SELECT   student_id,course_id,grade,
         row_number() OVER (PARTITION BY E.student_id ORDER BY grade DESC,course_id) AS r
FROM     Enrollments E) AS sub
WHERE    r=1

```

## Solution 2 Join
```sql
SELECT    student_id,MIN(course_id) AS course_id,grade
FROM (
SELECT    E2.student_id,course_id,E2.grade
FROM(
SELECT     student_id,MAX(grade) AS g
FROM       Enrollments AS E1
GROUP BY   student_id) AS sub1
INNER JOIN Enrollments AS E2
ON         sub1.g = E2.grade
WHERE      sub1.student_id = E2.student_id) AS sub2
GROUP BY   student_id,grade
ORDER BY   student_id
```
