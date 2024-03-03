# Basic Join

## Tasks:
1. The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of from your result.

```{SQL}
SELECT Hackers.hacker_id, Hackers.name, sum(max_score) AS total_score 
FROM (SELECT hacker_id, challenge_id, max(score) AS max_score
      FROM Submissions 
      GROUP BY hacker_id, challenge_id) AS score
JOIN Hackers 
ON score.hacker_id = Hackers.hacker_id
GROUP BY score.hacker_id, Hackers.name
HAVING total_score > 0
ORDER BY total_score DESC, score.hacker_id ASC;
```
<br/>
2. Harry Potter and his friends are at Ollivander's with Ron, finally replacing Charlie's old broken wand.
Hermione decides the best way to choose is by determining the minimum number of gold galleons needed to buy each non-evil wand of high power and age. Write a query to print the id, age, coins_needed, and power of the wands that Ron's interested in, sorted in order of descending power. If more than one wand has same power, sort the result in order of descending age.

```{SQL}
SELECT W.id, WP.age, W.coins_needed, W.power
FROM Wands  AS W
JOIN  Wands_Property AS WP 
ON W.code = WP.code
WHERE WP.is_evil = 0 
AND W.coins_needed = (SELECT MIN(W2.coins_needed) 
                        FROM Wands AS W2 
                        JOIN Wands_Property AS WP2 
                        ON W2.code = WP2.code 
                        WHERE W2.power = W.power 
                        AND WP2.age = WP.age 
                        AND WP2.is_evil = 0)
ORDER BY W.power DESC, WP.age DESC;
```
<br/>

3. Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.
Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```{SQL}
SELECT SUM(CITY.POPULATION) AS TOTALPOPULATION
FROM CITY
JOIN COUNTRY
ON CITY.CountryCode = COUNTRY.Code
WHERE COUNTRY.CONTINENT = 'Asia';
```
<br/>

4. Given the CITY and COUNTRY tables, query the names of all cities where the CONTINENT is 'Africa'.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```{SQL}
SELECT c.name
FROM CITY AS c
LEFT JOIN COUNTRY AS co
ON c.CountryCode = co.Code
WHERE CONTINENT = 'Africa';
```
<br/>

5. Given the CITY and COUNTRY tables, query the names of all the continents (COUNTRY.Continent) and their respective average city populations (CITY.Population) rounded down to the nearest integer.

Note: CITY.CountryCode and COUNTRY.Code are matching key columns.

```{SQL}
SELECT co.CONTINENT, FLOOR(AVG(c.population))
FROM CITY AS c
LEFT JOIN COUNTRY AS co
ON c.CountryCode = co.Code
WHERE co.CONTINENT IS NOT NULL
GROUP BY co.CONTINENT;
```
<br/>