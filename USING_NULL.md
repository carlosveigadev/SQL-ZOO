## Using Null

- List the teachers who have NULL for their department.

`SELECT name
FROM teacher
WHERE dept IS NULL`

- 2 Note the INNER JOIN misses the teachers with no department and the departments with no teacher.

`SELECT teacher.name AS Teacher, dept.name AS Dept
FROM teacher INNER JOIN dept ON (teacher.dept=dept.id)`

- 3 Use a different JOIN so that all teachers are listed.

`SELECT teacher.name AS Teacher, dept.name AS Dept
FROM teacher LEFT JOIN dept ON (teacher.dept=dept.id)`

- 4 Use a different JOIN so that all departments are listed.

`SELECT teacher.name AS Teacher, dept.name AS Dept
FROM teacher RIGHT JOIN dept ON (teacher.dept=dept.id)`

- 5 Use COALESCE to print the mobile number. Use the number '07986 444 2266' if there is no number given. Show teacher name and mobile number or '07986 444 2266'

``

- 6 

``

- 7

``

- 8

``

- 9

``

- 10

``