# hacker_rank_SQL
**Q:11**

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

**Answer**
select DISTINCT city from (SELECT T1.city FROM station T1 WHERE lower(SUBSTR(T1.city, -1)) not IN ('a', 'e', 'i', 'o', 'u') union all SELECT T1.city FROM station T1 WHERE lower(SUBSTR(T1.city, 0, 1)) not IN ('a', 'e', 'i', 'o', 'u'));

**Q:Weather Observation 19**

Consider  and  to be two points on a 2D plane where  are the respective minimum and maximum values of Northern Latitude (LAT_N) and  are the respective minimum and maximum values of Western Longitude (LONG_W) in STATION

**Answer**

select round(sqrt(power(max(LAT_N) - min(LAT_N), 2) + power(max(LONG_W) - min(LONG_W), 2)), 4) FROM STATION;

**Q:Weather Observation 20**

A median is defined as a number separating the higher half of a data set from the lower half. Query the median of the Northern Latitudes (LAT_N) from STATION and round your answer to  decimal places.

**Answer**
Select round(St.LAT_N,4) mediam from station St where (select count(Lat_N) from station where Lat_N < St.LAT_N ) = (select count(Lat_N) from station where Lat_N > St.LAT_N)
