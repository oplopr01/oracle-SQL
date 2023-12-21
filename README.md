

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



Quetion17:- REMOVE VOWELS FROM ENAMES

qUERY:-  SELECT REPLACE(TRANSLATE(UPPER(ENAME), 'AEIOU', 'AAAAA'),'A','') FROM EMP


--------------------------------------------------------------------------------------------------


Quetion18:-  COUNT THE NUMBER OF VOWELS IN EACH ENAMES

qUERY :- 
SELECT ENAME, LENGTH(ENAME)- LENGTH(REPLACE(TRANSLATE(UPPER(ENAME), 'AEIOU', 'AAAAA'),'A','')) AS VOWELcOUNT FROM EMP;


--------------------------------------------------------------------------------------------------


Question19:-  details of employee along with half term salary for the employee whose second character of the name is consonent

Query:- 
select emp.*, sal*6 as half_term_sal from emp where substr(ename,2,1) not in ('A','I','E','O','U');


--------------------------------------------------------------------------------------------------


Question20:- details of the employees who is earning maximum sal in each department

Query:- 


--------------------------------------------------------------------------------------------------


Question21:- middle 3 records from first half of the emp table

Query:-
select * from (select emp.*, rownum r from emp where rownum <= (select trunc(count(*)/2) from emp)) e1 where r between (select round(round(count(*)/2)/2) from emp )-1 and (select round(round(count(*)/2)/2) from emp )+1;


--------------------------------------------------------------------------------------------------


Question22:- display ename, job and deptname  should be present even if there are no employee or job in that perticular department

Query:- 
select ename, job , dname from dept left join emp on dept.deptno = emp.deptno;


--------------------------------------------------------------------------------------------------


Question23:- display ename, loc without using where clause

Query:-
select ename, loc from emp natural join dept;

--------------------------------------------------------------------------------------------------


Question24:- display ename, managers manager name and there locations
Query:- 

select e1.ename, e2.ename mgr, e3.ename managers_manager, d1.loc emp_loc , d2.loc mgr_loc from emp e1,emp e2, emp e3, dept d1, dept d2 where e1.mgr =e2.empno and e2.mgr = e3.empno and d1.deptno = e1.deptno and  d2.deptno = e3.deptno;


--------------------------------------------------------------------------------------------------


Question25:-  display middle 3 records from emp table

Query:-
select * from (select emp.*,rownum r from emp) where r between (select round(count(*)/2) from emp)-1 and  ((select round(count(*)/2) from emp)+1);


--------------------------------------------------------------------------------------------------

Question26:- display ename, job and location without using where clause

Query:-
 select ename, job, dname from emp join dept on emp.deptno = dept.deptno;


--------------------------------------------------------------------------------------------------

Question27:- display all the deptno along with the no of emp working in each department

Query:-
select deptno, count(*) from emp group by deptno;


--------------------------------------------------------------------------------------------------

Question28:- find number of vowels present in enames

Query:-
select ename,length(ename) - length(replace(replace(replace(replace(replace(ename,'A',''),'E',''),'I',''),'O',''),'U','')) FROM EMP;

SELECT ENAME , LENGTH(ENAME)- LENGTH(REPLACE(TRANSLATE(ENAME,'AEIOU','AAAAA'),'A','')) FROM EMP;


--------------------------------------------------------------------------------------------------


Question29:- display deptno and total number of employee working  where maxnumber of employee working

Query:-
SELECT * FROM (SELECT DEPTNO, COUNT(*) FROM EMP GROUP BY DEPTNO ORDER BY COUNT(*) DESC) WHERE ROWNUM =1 ;


--------------------------------------------------------------------------------------------------


Question30:- details of the employee whose earning maximum salary in each department

Query:-
select * from emp where sal in(select sal from (select max(sal) sal, deptno from emp group by deptno));

























