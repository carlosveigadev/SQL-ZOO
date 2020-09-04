## More JOIN operations

- 1 1962 movies

`SELECT id, title
 FROM movie
 WHERE yr=1962`

- 2 Give year of 'Citizen Kane'.

`SELECT yr
FROM movie
WHERE title = 'Citizen Kane'`

- 3 List all of the Star Trek movies, include the id, title and yr (all of these movies include the words Star Trek in the title). Order results by year.

`SELECT id, title, yr
FROM movie
WHERE title LIKE 'Star Trek%'
ORDER BY yr`

- 4  What id number does the actor 'Glenn Close' have?

SELECT id
FROM actor
WHERE name = 'Glenn Close'`

- 5 What is the id of the film 'Casablanca'

`SELECT id
FROM movie
WHERE title = 'Casablanca'`

- 6 Obtain the cast list for 'Casablanca'.

`SELECT name
FROM actor JOIN casting ON id = actorid
WHERE movieid = 11768`

- 7 Obtain the cast list for the film 'Alien'

`SELECT DISTINCT name
FROM actor JOIN casting ON id = actorid
WHERE movieid = (SELECT id
                 FROM movie
                 WHERE title = 'Alien')`

- 8 List the films in which 'Harrison Ford' has appeared

`SELECT DISTINCT title
FROM movie JOIN casting ON movieid = id
WHERE id IN (SELECT movieid
             FROM casting JOIN actor ON actorid = id
             WHERE name = 'Harrison Ford')`

- 9 List the films where 'Harrison Ford' has appeared - but not in the starring role. [Note: the ord field of casting gives the position of the actor. If ord=1 then this actor is in the starring role]

`SELECT DISTINCT title
FROM movie JOIN casting ON movieid = id
WHERE id IN (SELECT movieid
             FROM casting JOIN actor ON actorid = id
             WHERE name = 'Harrison Ford' AND ord != 1)`

- 10 List the films together with the leading star for all 1962 films.

`SELECT title, name
FROM movie 
         JOIN casting ON movie.id = movieid
         JOIN actor ON actorid = actor.id
WHERE yr = 1962 AND ord = 1  `

- 11 Which were the busiest years for 'Rock Hudson', show the year and the number of movies he made each year for any year in which he made more than 2 movies.

`SELECT yr,COUNT(title) FROM
  movie JOIN casting ON movie.id=movieid
        JOIN actor   ON actorid=actor.id
WHERE name='Rock Hudson'
GROUP BY yr
HAVING COUNT(title) > 2`

- 12 List the film title and the leading actor for all of the films 'Julie Andrews' played in.


`SELECT title, name
FROM movie JOIN casting ON movieid = movie.id AND ord = 1
           JOIN actor ON actorid = actor.id
WHERE movie.id IN (SELECT movieid FROM casting
                   WHERE actorid IN ( SELECT id 
                                      FROM actor
                                      WHERE name='Julie Andrews'))`

- 13 Obtain a list, in alphabetical order, of actors who've had at least 15 starring roles.


`SELECT name
FROM actor JOIN casting ON casting.actorid = actor.id
GROUP BY name
HAVING SUM(CASE ord WHEN 1 THEN 1 ELSE 0 END)>=15
ORDER BY name`

- 14 List the films released in the year 1978 ordered by the number of actors in the cast, then by title.

`SELECT title, COUNT(actorid)
FROM movie JOIN casting ON movie.id = casting.movieid
WHERE yr = 1978
GROUP BY title
ORDER BY COUNT(actorid) DESC, title ASC
`

- 15 List all the people who have worked with 'Art Garfunkel'.

`SELECT name
FROM actor JOIN casting ON casting.actorid = actor.id
WHERE movieid IN (SELECT movieid
                  FROM casting
                  WHERE actorid = (SELECT id
                                   FROM actor
                                   WHERE name = 'Art Garfunkel')) AND name <> 'Art Garfunkel'`

## QUIZ

- 1 
  
`SELECT name
  FROM actor INNER JOIN movie ON actor.id = director
 WHERE gross < budget`
- 2 

`SELECT *
  FROM actor JOIN casting ON actor.id = actorid
  JOIN movie ON movie.id = movieid`

- 3

`SELECT name, COUNT(movieid)
  FROM casting JOIN actor ON actorid=actor.id
 WHERE name LIKE 'John %'
 GROUP BY name ORDER BY 2 DESC` 
- 4

`Table-B
"Crocodile" Dundee
Crocodile Dundee in Los Angeles
Flipper
Lightning Jack`
- 5

`SELECT name
  FROM movie JOIN casting ON movie.id = movieid
  JOIN actor ON actor.id = actorid
WHERE ord = 1 AND director = 351`
- 6

`link the director column in movies with the primary key in actor
connect the primary keys of movie and actor via the casting table`
- 7

`Table-B
A Bronx Tale	1993
Bang the Drum Slowly	1973
Limitless	2011`