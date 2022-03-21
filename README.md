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

Query a list of CITY names from STATION for cities that have an even ID number. Print the results in any order, but exclude duplicates from the answer.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE ID%2=0

Find the difference between the total number of CITY entries in the table and the number of distinct CITY entries in the table. For example, if there are three records in the table with CITY values 'New York', 'New York', 'Bengalaru', there are 2 different city names: 'New York' and 'Bengalaru'. The query returns 1, because total# - unique# = 3 - 2 = 1
--------------------------------
SELECT COUNT(CITY) - COUNT(DISTINCT CITY)
FROM STATION

Query the two cities in STATION with the shortest and longest CITY names, as well as their respective lengths (i.e.: number of characters in the name). If there is more than one smallest or largest city, choose the one that comes first when ordered alphabetically. Sample Input: For example, CITY has four entries: DEF, ABC, PQRS and WXY.Sample Output: ABC 3 PQRS 4 Explanation: When ordered alphabetically, the CITY names are listed as ABC, DEF, PQRS, and WXY, with lengths 3 3 4 and 3. The longest name is PQRS, but there are 3 options for shortest named city. Choose ABC, because it comes first alphabetically. Note: You can write two separate queries to get the desired output. It need not be a single query.
--------------------------------
SELECT min(CITY), LENGTH(min(CITY))
FROM STATION
WHERE length(CITY) = (SELECT min(length(CITY)) FROM STATION)
UNION ALL
SELECT max(CITY), LENGTH(max(CITY))
FROM STATION
WHERE length(CITY) = (SELECT max(length(CITY)) FROM STATION)

Query the list of CITY names from STATION which have vowels (i.e., a, e, i, o, and u) as both their first and last characters. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[aeiou].*[aeiou]$';

Query the list of CITY names from STATION that do not start with vowels. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^(?![aeiou]).*'

Query the list of CITY names from STATION that do not end with vowels. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '.*[^aeiou]$';

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY 
FROM STATION
WHERE CITY REGEXP '^[^aeiou].*|.*[^aeiou]$';

Query the list of CITY names from STATION that do not start with vowels and do not end with vowels. Your result cannot contain duplicates.
--------------------------------
SELECT DISTINCT CITY
FROM STATION
WHERE CITY REGEXP '^[^aeiou].*[^aeiou]$';

Query the Name of any student in STUDENTS who scored higher than 75 Marks. Order your output by the last three characters of each name. If two or more students both have names ending in the same last three characters (i.e.: Bobby, Robby, etc.), secondary sort them by ascending ID.
--------------------------------
SELECT NAME
FROM STUDENTS
WHERE MARKS > 75
ORDER BY RIGHT (NAME, 3), ID ASC

Write a query that prints a list of employee names (i.e.: the name attribute) for employees in Employee having a salary greater than  per month who have been employees for less than  months. Sort your result by ascending employee_id.
--------------------------------
SELECT NAME
FROM EMPLOYEE
WHERE SALARY>2000 AND MONTHS<10
ORDER BY EMPLOYEE_ID ASC

Query the following two values from the STATION table: The sum of all values in LAT_N rounded to a scale of 2 decimal places. The sum of all values in LONG_W rounded to a scale of 2 decimal places.
--------------------------------
SELECT ROUND(SUM(LAT_N),2), ROUND(SUM(LONG_W),2)
FROM STATION

Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than 38.7880 and less than 137.2345. Truncate your answer to  decimal places.
--------------------------------
SELECT ROUND(SUM(LAT_N), 4)
FROM STATION
WHERE LAT_N < 137.2345 AND LAT_N > 38.7880
