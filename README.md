# SQL
SQL Notes

Query all columns for all American cities in the CITY table with populations larger than 100000. The CountryCode for America is USA.
--------------------------------
SELECT *
FROM CITY
WHERE POPULATION>100000 AND COUNTRYCODE = 'USA';


Query the list of CITY names starting with vowels (i.e., a, e, i, o, or u) from STATION. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[aeiou]';


Query the list of CITY names ending with vowels (a, e, i, o, u) from STATION. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '.*[aeiou]$';

Write a query that prints a list of employee names (i.e.: the name attribute) from the Employee table in alphabetical order. Where employee_id is an employee's ID number, name is their name, months is the total number of months they've been working for the company, and salary is their monthly salary.
--------------------------------
SELECT NAME FROM EMPLOYEE 
ORDER BY NAME ASC
