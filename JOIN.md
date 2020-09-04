## The JOIN operation

- 1 Modify it to show the matchid and player name for all goals scored by Germany. To identify German players, check for: teamid = 'GER'


`SELECT matchid, player
FROM goal 
WHERE teamid LIKE 'GER'`

- 2 Show id, stadium, team1, team2 for just game 1012


`SELECT id,stadium,team1,team2
  FROM game
   WHERE id LIKE '1012'`

- 3 Modify it to show the player, teamid, stadium and mdate for every German goal.


`SELECT player, teamid, stadium, mdate
  FROM game JOIN goal ON (id=matchid)
   WHERE teamid LIKE 'GER'`

- 4 Show the team1, team2 and player for every goal scored by a player called Mario player LIKE 'Mario%'

`SELECT team1, team2, player
FROM game JOIN goal ON (id=matchid)
WHERE player LIKE 'Mario%'
`

- 5 Show player, teamid, coach, gtime for all goals scored in the first 10 minutes gtime<=10


`SELECT player, teamid, coach, gtime
  FROM goal JOIN eteam on teamid=id
 WHERE gtime<=10`

- 6 List the dates of the matches and the name of the team in which 'Fernando Santos' was the team1 coach.

`SELECT mdate, teamname
FROM game JOIN eteam ON (team1=eteam.id)
WHERE coach LIKE 'Fernando Santos'`

- 7 List the player for every goal scored in a game where the stadium was 'National Stadium, Warsaw'

`SELECT player
FROM game JOIN goal ON matchid=id
WHERE stadium LIKE 'National Stadium, Warsaw'`

- 8 Instead show the name of all players who scored a goal against Germany.

`SELECT DISTINCT player 
FROM game JOIN goal ON matchid = id 
WHERE (teamid!='GER' AND (team1='GER' OR team2='GER'))`

- 9 Show teamname and the total number of goals scored.

`SELECT teamname, COUNT(teamid)
  FROM eteam JOIN goal ON id=teamid
 GROUP BY teamname`

- 10 Show the stadium and the number of goals scored in each stadium.

`SELECT stadium, COUNT(*)
  FROM game JOIN goal ON id=matchid
 GROUP BY stadium`

- 11 For every match involving 'POL', show the matchid, date and the number of goals scored.

`SELECT matchid, mdate, COUNT(gtime)
  FROM game JOIN goal ON matchid = id 
 WHERE (team1 = 'POL' OR team2 = 'POL')
GROUP BY matchid, mdate`

- 12 For every match where 'GER' scored, show matchid, match date and the number of goals scored by 'GER'

`SELECT matchid, mdate, COUNT(teamid) AS goals
FROM game JOIN goal ON matchid = id
WHERE goal.teamid = 'GER'
GROUP BY matchid, mdate`

- 13 Sort your result by mdate, matchid, team1 and team2.

`SELECT mdate, 
  team1, SUM(CASE WHEN teamid=team1 THEN 1 ELSE 0 END) score1,
  team2, SUM(CASE WHEN teamid=team2 THEN 1 ELSE 0 END) score2
  FROM game JOIN goal ON matchid = id
GROUP BY mdate, team1, team2
`

## QUIZ

- 1 

`game  JOIN goal ON (id=matchid)`

- 2

`matchid, teamid, player, gtime, id, teamname, coach`

- 3

`SELECT player, teamid, COUNT(*)
  FROM game JOIN goal ON matchid = id
 WHERE (team1 = "GRE" OR team2 = "GRE")
   AND teamid != 'GRE'
 GROUP BY player, teamid`

- 4

`DEN	9 June 2012
GER	9 June 2012`

- 5

` FROM game JOIN goal ON matchid = id 
  WHERE stadium = 'National Stadium, Warsaw' 
 AND (team1 = 'POL' OR team2 = 'POL')
   AND teamid != 'POL'`

- 6

`SELECT DISTINCT player, teamid, gtime
  FROM game JOIN goal ON matchid = id
 WHERE stadium = 'Stadion Miejski (Wroclaw)'
   AND (( teamid = team2 AND team1 != 'ITA') OR ( teamid = team1 AND team2 != 'ITA'))`

- 7

`Netherlands	2
Poland	2
Republic of Ireland	1
Ukraine	2`
 