SELECT from Nobel Tutorial

1. Change the query to display the 1950 Nobel prize information.

SELECT yr, subject, winner
  FROM nobel
 WHERE yr = 1950
 

2. show who won the 1962 Prize for Literature (Literature).

SELECT winner
  FROM nobel
 WHERE yr = 1962
   AND subject = 'Literature'
 

3. Display "Einstein" ( 'Albert Einstein') of the year award and awards.
 

SELECT yr, subject 
  FROM nobel
WHERE winner = 'Albert Einstein'
 

4. Display ( 'Peace') winners in 2000 and later Peace Prize.

SELECT winner 
  FROM nobel
WHERE yr >= 2000 AND subject = 'Peace';
 

5. show from 1980 to 1989 (inclusive included) literary prize (Literature) winner all the details (of the theme, the winners).

SELECT yr, subject, winner 
  FROM nobel
WHERE subject = 'Literature' AND yr >= 1980 AND yr <= 1989
ORDER BY yr;
 

6. display all details of the president's winners:

• Theodore Roosevelt
• Woodrow Wilson
• Jimmy Carter 
• Barack Obama
SELECT * FROM nobel
 WHERE  winner IN ('Theodore Roosevelt', 
                  'Woodrow Wilson', 
                  'Jimmy Carter', 
                  'Barack Obama')
 

7. Display name for John the winners. (Note: foreigners name (First name) first, Surname (Last name) after)

SELECT winner 
  FROM nobel
WHERE winner LIKE 'John%';
 

8. Display 1980 physics (physics) winners, and the 1984 Prize in Chemistry (chemistry) winner.

SELECT yr, subject, winner 
  FROM nobel
WHERE yr = 1980 AND subject = 'physics' 
  OR (yr = 1984 AND subject = 'chemistry' );

9. View the 1980 winners, but excluding Prize in Chemistry (Chemistry) and the Prize for Medicine (Medicine).

SELECT yr, subject, winner 
  FROM nobel
WHERE yr= 1980 
  AND subject NOT IN('Chemistry', 'Medicine');
 

10. The display early Prize in Medicine (Medicine) Winner (before 1910, excluding 1910), and in recent years Prize in Literature (Literature) winner (after 2004, including in 2004).

SELECT *
  FROM nobel
WHERE subject = 'Medicine' AND yr < 1910
  OR subject = 'Literature' AND yr >= 2004;

11. Find all details of the prize won by PETER GRÜNBERG

SELECT *
 FROM nobel
WHERE winner = 'PETER GRÜNBERG';
 

12. • Find Eugene O'Neill EUGENE O'NEILL winning all the details Find all details of the prize won by EUGENE O'NEILL

*string requires two single quotes for the apostrophe*

SELECT *
 FROM nobel
WHERE winner = 'EUGENE O''NEILL';


 

13. Knight lined Knights in order

Sir lists of winners, year, prize page (Lord's name begins with Sir). First display the latest winners, and then press the name of the same year arrangement order.

SELECT winner, yr, subject 
  FROM nobel
WHERE winner LIKE 'Sir%'
ORDER BY yr desc, winner
 

14. The expression subject IN ('Chemistry','Physics') can be used as a value - it will be 0 or 1.

Show the 1984 winners and subject ordered by subject and winner name; but list Chemistry and Physics last.

SELECT winner, subject 
  FROM nobel
WHERE yr = 1984
ORDER BY 
CASE WHEN subject IN ( 'Chemistry', 'Physics') THEN 1 ELSE 0, subject, winner ;
 

