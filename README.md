# hacker_rank_SQL
**Q:Weather Observation 2**

Query the following two values from the STATION table:

The sum of all values in LAT_N rounded to a scale of  decimal places.
The sum of all values in LONG_W rounded to a scale of  decimal places.

**Answer**

SELECT ROUND(SUM(LAT_N), 2), ROUND(SUM(LONG_W), 2) FROM STATION

**Q:11**

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

**Answer**
select DISTINCT city from (SELECT T1.city FROM station T1 WHERE lower(SUBSTR(T1.city, -1)) not IN ('a', 'e', 'i', 'o', 'u') union all SELECT T1.city FROM station T1 WHERE lower(SUBSTR(T1.city, 0, 1)) not IN ('a', 'e', 'i', 'o', 'u'));

**Q:Types of Triangle**

Write a query identifying the type of each record in the TRIANGLES table using its three side lengths. Output one of the following statements for each record in the table:

Equilateral: It's a triangle with  sides of equal length.
Isosceles: It's a triangle with  sides of equal length.
Scalene: It's a triangle with  sides of differing lengths.
Not A Triangle: The given values of A, B, and C don't form a triangle.

**Answer**

SELECT CASE
WHEN A + B <= C OR A + C <= B OR B + C <= A THEN 'Not A Triangle'
WHEN A = B AND B = C THEN 'Equilateral'
WHEN A = B OR B = C OR A = C THEN 'Isosceles'
ELSE 'Scalene'
END
FROM TRIANGLES;

**Q:japan Population**

Query the sum of the populations for all Japanese cities in CITY. The COUNTRYCODE for Japan is JPN.

**Answer**
SELECT SUM(POPULATION) FROM CITY WHERE COUNTRYCODE='JPN'

**Q:Weather Observation 13**

Query the sum of Northern Latitudes (LAT_N) from STATION having values greater than  and less than . Truncate your answer to  decimal places.

**Answer**

SELECT ROUND(SUM(LAT_N),4) FROM STATION WHERE LAT_N > 38.7880 AND LAT_N < 137.2345;

**Q:Weather Observation 14**
Query the greatest value of the Northern Latitudes (LAT_N) from STATION that is less than . Truncate your answer to  decimal places.

**Answer**

SELECT ROUND(MAX(LAT_N),4) FROM STATION WHERE LAT_N < 137.2345;

**Q:Weather Observation 15**

Query the Western Longitude (LONG_W) for the largest Northern Latitude (LAT_N) in STATION that is less than . Round your answer to  decimal places.

**Answer**

SELECT ROUND(LONG_W,4) FROM STATION WHERE LAT_N = (SELECT MAX(LAT_N) FROM STATION WHERE LAT_N < 137.2345)

**Q:Weather Observation 16**

Query the smallest Northern Latitude (LAT_N) from STATION that is greater than . Round your answer to  decimal places.

**Answer**
SELECT ROUND(MIN(LAT_N),4) FROM STATION WHERE LAT_N > 38.7780

**Q:Weather Observation 17**

Query the Western Longitude (LONG_W)where the smallest Northern Latitude (LAT_N) in STATION is greater than . Round your answer to  decimal places.

**Answer**

SELECT ROUND(LONG_W,4) FROM STATION WHERE LAT_N = ( SELECT MIN(LAT_N) FROM STATION WHERE LAT_N > 38.7780)

Q:Top Earning

We define an employee's total earnings to be their monthly  worked, and the maximum total earnings to be the maximum total earnings for any employee in the Employee table. Write a query to find the maximum total earnings for all employees as well as the total number of employees who have maximum total earnings. Then print these values as  space-separated integers.

**Answer**

select months*salary, count(*) from employee group by months*salary order by months*salary desc limit 1


