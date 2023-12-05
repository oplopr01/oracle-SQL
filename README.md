

--------------------------------------------------------------------------------------------------

Question1:- Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.  [HackerRankQuestion]

Query1:-
select distinct(city from station where city like '%a' or city like '%e' or city like '%i' or city like '%u' or city like '%o';

Query2:- 
select distinct city from station where substr(city, -1, 1) in('a','e','i','o','u');


--------------------------------------------------------------------------------------------------

Question2:-  Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.

Query1:- 
select distinct city from station where substr(CITY, 1, 1) not in('A','E','I','O','U');



--------------------------------------------------------------------------------------------------

Question3:-  Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.

Query1:- 
select distinct city from station where substr(CITY, -1, 1) not in('A','E','I','O','U');



--------------------------------------------------------------------------------------------------

Question4:- Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

Query1:- 
select distinct city from station where substr(CITY, -1, 1) not in('a','e','i','o','u') or substr(CITY, 1, 1) not in('A','E','I','O','U');


--------------------------------------------------------------------------------------------------

Question5:-  Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.

Query1:- 
select distinct city from station where substr(CITY, -1, 1) not in('a','e','i','o','u') and substr(CITY, 1, 1) not in('A','E','I','O','U');



--------------------------------------------------------------------------------------------------

Question6:-  Query the Name of any student in STUDENTS who scored higher than  Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.

Query1:- 
select name from Students where marks >75 order by substr(name,-3,3),id; 
[it will order by last chars in case of tie it will prefer ID for shorting]


--------------------------------------------------------------------------------------------------



Question7:-  Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order.

Query1:- 
select name from employee order by name;


--------------------------------------------------------------------------------------------------

Question8:- Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than  per month who have been employees for less than  months. Sort your result by ascending employee_id.

Query:- 
select name from employee where salary >2000 and months<10 order by employee_id;


--------------------------------------------------------------------------------------------------



Question9:-  Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically.

Query:- 
SELECT CITY, LENGTH(CITY) AS CITY_LENGTH
FROM STATION
WHERE LENGTH(CITY) = (
    SELECT MIN(LENGTH(CITY))
    FROM STATION
)
ORDER BY CITY




--------------------------------------------------------------------------------------------------

Question10;- Query a count of the number of cities in CITY having a Population larger than 100000

Query:- 
select count(name) from city where population > 100000;



--------------------------------------------------------------------------------------------------



Quetion11:- Query the total population of all cities in CITY where District is California.
Query:- 
select sum(population) from city where district = 'California';





--------------------------------------------------------------------------------------------------



Quetion12:- Query the average population of all cities in CITY where District is California.

Query:- 
select avg(population) from city where district = 'California';






--------------------------------------------------------------------------------------------------



Quetion13:- Query the average population for all cities in CITY, rounded down to the nearest integer.

Query:-
select round(avg(population)) from city;



--------------------------------------------------------------------------------------------------



Quetion14:- Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

Query:- 
select sum(population) from city where countrycode = 'JPN';





--------------------------------------------------------------------------------------------------



Quetion15:- Query the difference between the maximum and minimum populations in CITY.

Query:-
select max(population) - min(population) from city;





--------------------------------------------------------------------------------------------------



Quetion16:- We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

Query:- 
select max(salary* months) as totalSal, count(*) from employee where (salary*months)= (select max(salary*months) from employee);





--------------------------------------------------------------------------------------------------



Quetion17:- 




































