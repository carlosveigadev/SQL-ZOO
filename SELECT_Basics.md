## Introducing the `world` table of countries

- Modify it to show the population of Germany


`SELECT population FROM world
  WHERE name = 'Germany'`

- Show the name and the population for 'Sweden', 'Norway' and 'Denmark'.

`SELECT name, population FROM world
  WHERE name IN ('Sweden', 'Norway', 'Denmark');`

- Modify it to show the country and the area for countries with an area between 200,000 and 250,000.
  
`SELECT name, area FROM world
  WHERE area BETWEEN 200000 AND 250000`

### QUIZ
- 1 
  
`SELECT name, population
  FROM world
 WHERE population BETWEEN 1000000 AND 1250000`

- 2

`Table-E
Albania	3200000
Algeria	32900000`

- 3

`SELECT name FROM world
 WHERE name LIKE '%a' OR name LIKE '%l'`

- 4 

`name	length(name)
Italy	5
Malta	5
Spain	5`  

- 5

`Andorra	936` 

- 6 

`SELECT name, area, population
  FROM world
 WHERE area > 50000 AND population < 10000000`

- 7

`SELECT name, population/area
  FROM world
 WHERE name IN ('China', 'Nigeria', 'France', 'Australia')` 


   

