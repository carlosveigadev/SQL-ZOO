## SELECT from Nobel 

- Change the query shown so that it displays Nobel prizes for 1950.

`SELECT yr, subject, winner
  FROM nobel
 WHERE yr = 1950`

- Show who won the 1962 prize for Literature.

`SELECT winner
FROM nobel
WHERE yr = 1962
AND subject = 'Literature'`

- Show the year and subject that won 'Albert Einstein' his prize.

`SELECT yr, subject
FROM nobel 
WHERE winner = 'Albert Einstein'`

- Give the name of the 'Peace' winners since the year 2000, including 2000.

`SELECT winner
FROM nobel 
WHERE subject = 'Peace' AND yr >= 2000`

- Show all details (yr, subject, winner) of the Literature prize winners for 1980 to 1989 inclusive.

`SELECT *
FROM nobel
WHERE subject = 'Literature' AND yr BETWEEN 1980 AND 1989`

- Show all details of the presidential winners:

- Theodore Roosevelt
- Woodrow Wilson
- Jimmy Carter
- Barack Obama

`SELECT * 
FROM nobel
WHERE winner IN ('Theodore Roosevelt', 'Woodrow Wilson', 'Jimmy Carter', 'Barack Obama')`

- Show the winners with first name John

`SELECT winner
FROM nobel
WHERE winner LIKE 'John%'`

- Show the year, subject, and name of Physics winners for 1980 together with the Chemistry winners for 1984.

`SELECT *
FROM nobel
WHERE subject = 'Physics' AND yr = 1980 
OR subject = 'Chemistry' AND yr = 1984`

- Show the year, subject, and name of winners for 1980 excluding Chemistry and Medicine

`SELECT *
FROM nobel 
WHERE subject NOT IN ('Chemistry', 'Medicine') AND yr = 1980`

- Show year, subject, and name of people who won a 'Medicine' prize in an early year (before 1910, not including 1910) together with winners of a 'Literature' prize in a later year (after 2004, including 2004)

`SELECT *
FROM nobel
WHERE (subject = 'Literature' AND yr > 2003)
OR (subject = 'Medicine' AND yr < 1910) 
`

- Find all details of the prize won by PETER GRÜNBERG

`SELECT *
FROM nobel
WHERE winner = 'PETER GRÜNBERG'`

- Find all details of the prize won by EUGENE O'NEILL

`SELECT *
FROM nobel
WHERE winner = 'Eugene O''Neill'`

- Knights in order
- List the winners, year and subject where the winner starts with Sir. Show the the most recent first, then by name order.

`SELECT winner, yr, subject
FROM nobel
WHERE winner LIKE 'Sir%'
ORDER BY yr DESC`

- The expression subject IN ('Chemistry','Physics') can be used as a value - it will be 0 or 1.
- Show the 1984 winners and subject ordered by subject and winner name; but list Chemistry and Physics last.
  
`SELECT winner, subject
  FROM nobel
 WHERE yr=1984
 ORDER BY 
CASE WHEN subject IN ('Physics','Chemistry') THEN 1 ELSE 0 END, subject, winner`

## QUIZ

- 1

`SELECT winner FROM nobel
 WHERE winner LIKE 'C%' AND winner LIKE '%n'`

- 2

`SELECT COUNT(subject) FROM nobel
 WHERE subject = 'Chemistry'
   AND yr BETWEEN 1950 and 1960`

- 3

`SELECT COUNT(DISTINCT yr) FROM nobel
 WHERE yr NOT IN (SELECT DISTINCT yr FROM nobel WHERE subject = 'Medicine')`

- 4

`Medicine	Sir John Eccles
Medicine	Sir Frank Macfarlane Burnet
`

- 5

`SELECT yr FROM nobel
 WHERE yr NOT IN(SELECT yr 
                   FROM nobel
                 WHERE subject IN ('Chemistry','Physics'))`
- 6

`SELECT DISTINCT yr
  FROM nobel
 WHERE subject='Medicine' 
   AND yr NOT IN(SELECT yr FROM nobel 
                  WHERE subject='Literature')
   AND yr NOT IN (SELECT yr FROM nobel
                   WHERE subject='Peace')`

- 7 

`Chemistry	1
Literature	1
Medicine	2
Peace	1
Physics	1`

