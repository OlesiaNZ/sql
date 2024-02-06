# Basic Select

## Tasks:
1. Query all columns for all American cities in the CITY table with populations larger than 100000. 
The CountryCode for America is USA. 
```{SQL}
SELECT *
FROM CITY
WHERE COUNTRYCODE = "USA"
AND POPULATION > 100000;
```
<br/>

2. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
```{SQL}
SELECT NAME
FROM CITY 
WHERE COUNTRYCODE = "USA" AND 
POPULATION > 120000;
```
<br/>

3. Query all columns for a city in CITY with the ID 1661
```{SQL}
SELECT *
FROM CITY 
WHERE ID = 1661;
```
<br/>

4. Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
```{SQL}
SELECT *
FROM CITY
WHERE COUNTRYCODE = "JPN";
```
<br/>

5. Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN. 
```{SQL}
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = "JPN";
```
<br/>

6. Query a list of CITY and STATE from the STATION table.
```{SQL}
SELECT CITY, STATE
FROM STATION;
```
<br/>

7. Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
```{SQL}
SELECT DISTINCT CITY
FROM STATION
WHERE MOD(ID, 2) = 0;
```
<br/>

8. Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table.
```{SQL}
SELECT COUNT(CITY) - COUNT (DISTINCT CITY) AS Difference
FROM STATION;
```
<br/>

9. Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically. 
```{SQL}
SELECT CITY, LENGTH(CITY) AS City_len
FROM STATION
ORDER BY City_len DESC, CITY
FETCH FIRST ROW ONLY;

SELECT CITY, LENGTH(CITY) AS City_len
FROM STATION
ORDER BY City_len, CITY 
FETCH FIRST ROW ONLY;
```
<br/>

10. Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE 'A%' OR CITY LIKE 'E%' OR CITY LIKE 'I%' OR CITY LIKE 'O%' OR CITY LIKE 'U%';
``` 
<br/>

11. Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION
WHERE CITY LIKE '%a' OR CITY LIKE '%e' OR CITY LIKE '%i' OR CITY LIKE '%o' OR CITY LIKE '%u';
```
<br/>

12. Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION
WHERE LOWER(SUBSTR(CITY, 1, 1)) IN ('a', 'e', 'i', 'o', 'u')
  AND LOWER(SUBSTR(CITY, LENGTH(CITY), 1)) IN ('a', 'e', 'i', 'o', 'u');
```
<br/>

13. Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT LIKE 'A%' AND CITY NOT LIKE 'E%' AND CITY NOT LIKE 'I%' AND CITY NOT LIKE 'O%' AND CITY NOT LIKE 'U%';
```
<br/>

14. Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION
WHERE CITY NOT LIKE '%a' AND CITY NOT LIKE '%e' AND CITY NOT LIKE '%i' AND CITY NOT LIKE '%o' AND CITY NOT LIKE '%u';
```
<br/>

15. Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION 
WHERE LOWER(SUBSTR(CITY, 1, 1)) NOT IN ('a', 'e', 'i', 'o', 'u')
  OR LOWER(SUBSTR(CITY, LENGTH(CITY), 1)) NOT IN ('a', 'e', 'i', 'o', 'u');
```
<br/>

16. Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
```{SQL}
SELECT DISTINCT CITY
FROM STATION 
WHERE LOWER(SUBSTR(CITY, 1, 1)) NOT IN ('a', 'e', 'i', 'o', 'u')
AND LOWER(SUBSTR(CITY, LENGTH(CITY), 1)) NOT IN ('a', 'e', 'i', 'o', 'u');
```
<br/>

17. Query the Name of any student in STUDENTS who scored higher than Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
```{SQL}
SELECT Name
FROM STUDENTS
WHERE Marks > 75
ORDER BY RIGHT(Name, 3), ID;
```
<br/>

18. Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.
```{SQL}
SELECT name
FROM Employee
ORDER BY name;
```
<br/>

19. Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than $2000 per month who have been employees for less than 10 months. Sort your result by ascending employee_id.
```{SQL}
SELECT name
FROM Employee
WHERE salary > 2000 AND months < 10
ORDER BY employee_id;
```
<br/>