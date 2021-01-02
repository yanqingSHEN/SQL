###   Question Link：[Leetcode/Consecutive Available Seats](https://leetcode.com/problems/consecutive-available-seats/)


```sql
SELECT      DISTINCT C1.seat_id
FROM        cinema C1
JOIN        cinema C2
ON          C2.seat_id = C1.seat_id+1 OR C2.seat_id  = C1.seat_id-1
WHERE       C1.free = 1 AND C2.free = 1
ORDER BY    C1.seat_id,C2.seat_id
```
