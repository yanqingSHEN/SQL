### Link: (https://sqlzoo.net/wiki/More_JOIN_operations)

##  List the film title and the leading actor for all of the films 'Julie Andrews' played in.

```sql
SELECT title,name
FROM   movie JOIN casting ON movie.id=movieid
             JOIN actor   ON actorid=actor.id
WHERE  movie.id IN
(
SELECT movieid FROM casting JOIN movie ON movieid=id
WHERE actorid IN (
  SELECT id FROM actor
  WHERE name='Julie Andrews'))
AND ord = 1
```
