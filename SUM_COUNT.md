## SUM and COUNT Tutorial

- 1 Show the total population of the world.

`SELECT SUM(population)
FROM world`

- 2 List all the continents - just once each.

`SELECT DISTINCT continent
FROM world`

- 3 Give the total GDP of Africa

`SELECT SUM(gdp)
FROM world
WHERE continent = 'Africa'`

- 4 How many countries have an area of at least 1000000

`SELECT COUNT(name)
FROM world
WHERE area > 1000000`

- 5 What is the total population of ('Estonia', 'Latvia', 'Lithuania')

`SELECT SUM(population)
FROM world
WHERE name IN ('Estonia', 'Latvia', 'Lithuania')`

- 6 For each continent show the continent and number of countries.

` SELECT continent, COUNT(name)
FROM world 
GROUP BY continent ` 

- 7 For each continent show the continent and number of countries with populations of at least 10 million.

`SELECT continent, COUNT(name)
FROM world
WHERE population > 10000000
GROUP BY continent`

- 8 List the continents that have a total population of at least 100 million.

`SELECT continent
FROM world
GROUP BY continent
HAVING SUM(population) > 100000000`

## QUIZ

- 1

` SELECT SUM(population) FROM bbc WHERE region = 'Europe'`
- 2

`SELECT COUNT(name) FROM bbc WHERE population < 150000`
- 3

`AVG(), COUNT(), MAX(), MIN(), SUM()`
- 4

`No result due to invalid use of the WHERE function`
- 5

`SELECT AVG(population) FROM bbc WHERE name IN ('Poland', 'Germany', 'Denmark')`
- 6

` SELECT region, SUM(population)/SUM(area) AS density FROM bbc GROUP BY region`
- 7

`SELECT name, population/area AS density FROM bbc WHERE population = (SELECT MAX(population) FROM bbc)`

- 8

`Table-D
Americas	732240
Middle East	13403102
South America	17740392
South Asia	9437710`
  