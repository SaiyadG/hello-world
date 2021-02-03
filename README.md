# hello-world

Tutorial - Create New Repo

SAMPLE BASIC CODING

USE Movies (Database)

SELECT
/* TAB KEY-  Name of Column -   
AS - Alias, also known as..  you dont have to write this , but good so you understand the flow of code*/

  FilmName TITLE,
  Film Duration 'Released on' ,
  
  /* the above statemnent can also be written like
  FilmName AS [TITLE],
  Film Duration AS [Released On],
  */
  
FROM
  Table Name

WHERE 

*/ WHERE STATEMENT ADDED UNDER FROM STATEMENT
WHERE criteria:
< lESS THAN
> GREATHER THAN
>= GREATH THAN OR EQUAL TOO
<= LESS THAN OR EQUAL TOO
<> not equaltoo
BETWEEN value1  AND  value 2
IN (10, 20.30)   -(range of numbers you want)  /*

*/ SEARCHING FOR NUMERICAL DATA/*

  FilmRunTimeMinutes = 120   (check row 25 for criterias)
  FilmRunTimeMinutes >= 120 
  
*/ search BETWEEN / AND  cetain range, see row 31/*

  FilmRunTimeMinutes BETWEEN 120 AND 150

*/ Using IN () to search for only those numbers /*

  FilmRunTimeMinutes IN (10,50,100,180)
  
  */Search Date using Date field/* 
DAY (FilmReleaseDate)= '22'
MONTH (FilmReleaseDate)='5'
YEAR (FilmReleaseDate)='2018'

*/ 
> - After date
< - before date 
/*
  
 */ TEXT CRITERIAS in WHERE Claus /*

*/ Searching by name /*

WHERE
  Filmname = 'Harry Potter'
  
*/USING WILDCARDS WITH Text
LIKE - Add wildcard character % _
NOT LIKE - doesnt show that record when searching/*

WHERE
  Filmname LIKE 'Harry Potter'  
       */ add WILDCARD % __  /*
       
  Filmname LIKE 'Harry Potter%'  */ this will show all movies starting with Harry Potter followed by anything else after /*
  Filmname LIKE '%Harry Potter%' */ this will show all movies with Harry Potter anywhere in the title /*
  Filmname LIKE 'Harry Potter__' */ each individual underscore used represented space, character or number /*
  
*/ NOT LIKE, will not search that movie in the database, below query will show all movies except Harry Potter /*  

WHERE
  Filmname NOT LIKE '%Harry Potter%'
  
  ORDER BY
*/ ASC - Ascending  
DESC - Descending /*


