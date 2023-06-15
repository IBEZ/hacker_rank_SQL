# hacker_rank_SQL
**Q:11**

Query the list of CITY names from STATION that either do not start with vowels or do not end with vowels. Your result cannot contain duplicates.

**Answer**
select DISTINCT city from (SELECT T1.city FROM station T1 WHERE lower(SUBSTR(T1.city, -1)) not IN ('a', 'e', 'i', 'o', 'u') union all SELECT T1.city FROM station T1 WHERE lower(SUBSTR(T1.city, 0, 1)) not IN ('a', 'e', 'i', 'o', 'u'));
