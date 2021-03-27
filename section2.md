SELECT from WORLD Tutorial

1. Observe the result of running this SQL command to show the name, continent and population of all countries.

SELECT name, continent, population 
FROM world

2. Show the name for the countries that have a population of at least 200 million. 200 million is 200000000, there are eight zeros.

SELECT name FROM world
WHERE population >= 200000000

3. Give the name and the per capita GDP for those countries with a population of at least 200 million
.
SELECT name,GDP/population 
FROM world
WHERE population >= 200000000

4. Show the name and population in millions for the countries of the continent ‘South America’. Divide the population by 1000000 to get population in millions.
SELECT name,population/1000000 as population 
FROM world
WHERE continent = 'South America'

5. Show the name and population for France, Germany, Italy

SELECT name,population 
FROM world
WHERE name in ('France','Germany','Italy')

6. Show the countries which have a name that includes the word ‘United’

SELECT name FROM world
WHERE name like '%United%'


7. Show the countries that are big by area or big by population. Show name, population and area.
SELECT name,population,area 
FROM world
WHERE area > 3000000 or population > 250000000

8. Exclusive OR (XOR). Show the countries that are big by area (more than 3 million) or big by population (more than 250 million) but not both. Show name, population and area.
Australia has a big area but a small population, it should be
included.
Indonesia has a big population but a small area, it should be included.
China has a big population and big area, it should be excluded.
United Kingdom has a small population and a small area, it should be excluded.

```
SELECT name, population, area 
FROM world 
WHERE (area > 3000000 AND population < 250000000) OR (population > 250000000 AND area < 3000000);
```
SELECT name,population,area 
FROM world
WHERE area > 3000000 xor population > 250000000

9. For South America show population in millions and GDP in billions both to 2 decimal places.
Millions and billions
Divide by 1000000 (6 zeros) for millions. Divide by 1000000000 (9 zeros) for billions.

SELECT name,round(population/1000000,2) as population,round(GDP/1000000000,2) as GDP 
FROM world
WHERE continent = 'South America'

10. Show per-capita GDP for the trillion dollar countries to the nearest $1000.


SELECT name, ROUND(gdp/population, -3)
FROM world 
WHERE GDP > 1000000000000


11. Show the name and capital where the name and the capital have the same number of characters.
You can use the LENGTH function to find the number of characters in a string

SELECT name, capital
FROM world
WHERE LENGTH(name)= LENGTH(capital)

12. Show the name and the capital where the first letters of each match. Don’t include countries where the name and the capital are the same word
You can use the function LEFT to isolate the first character.
You can use <> as the NOT EQUALS operator.

SELECT name, capital
FROM world
WHERE  LEFT(name,1)=LEFT(capital,1) and name<>capital


13. Find the country that has all the vowels and no spaces in its name.
Equatorial Guinea and Dominican Republic have all of the vowels (a e i o u) in the name. They don’t count because they have more than one word in the name.
You can use the phrase name NOT LIKE ‘%a%’ to exclude characters from your results.
The query shown misses countries like Bahamas and Belarus because they contain at least one ‘a’

SELECT name
   FROM world
WHERE name LIKE '%a%' 
	AND name LIKE '%e%' 
	AND name LIKE '%i%' 
	AND name LIKE '%o%' 
	AND name LIKE '%u%'
  AND name NOT LIKE '% %'