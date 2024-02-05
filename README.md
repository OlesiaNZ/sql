# Practice in SQL online

## Tasks:
1. Query all columns for all American cities in the CITY table with populations larger than 100000. 
The CountryCode for America is USA. 
```{SQL}
SELECT *
FROM CITY
WHERE COUNTRYCODE = "USA"
AND POPULATION > 100000;
```
2. Query the NAME field for all American cities in the CITY table with populations larger than 120000. The CountryCode for America is USA.
```{SQL}
SELECT NAME
FROM CITY 
WHERE COUNTRYCODE = "USA" AND 
POPULATION > 120000;
```
3. Query all columns for a city in CITY with the ID 1661
```{SQL}
SELECT *
FROM CITY 
WHERE ID = 1661;
```
4. Query all attributes of every Japanese city in the CITY table. The COUNTRYCODE for Japan is JPN.
```{SQL}
SELECT *
FROM CITY
WHERE COUNTRYCODE = "JPN";
```
5. Query the names of all the Japanese cities in the CITY table. The COUNTRYCODE for Japan is JPN. 
```{SQL}
SELECT NAME
FROM CITY
WHERE COUNTRYCODE = "JPN";
```
