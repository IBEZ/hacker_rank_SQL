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

**Q:Asian Countries**

Given the CITY and COUNTRY tables, query the sum of the populations of all cities where the CONTINENT is 'Asia'.

**Answer**

SELECT SUM(City.population) FROM Country INNER JOIN City  ON Country.Code = City.CountryCode WHERE Country.Continent='Asia';

**Q:Placement**

You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).

**Answer**

Select S.Name From ( Students S join Friends F using(ID) join Packages P1 on S.ID=P1.ID join Packages P2 on F.Friend_ID=P2.ID) Where P2.Salary > P1.Salary Order By P2.Salary

**Q:Interview**

Samantha interviews many candidates from different colleges using coding challenges and contests. Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, total_views, and total_unique_views for each contest sorted by contest_id. Exclude the contest from the result if all four sums are .

Note: A specific contest can be used to screen candidates at more than one college, but each college only holds  screening contest.

**Answer**

SELECT con.contest_id, con.hacker_id, con.name, SUM(sg.total_submissions), SUM(sg.total_accepted_submissions), SUM(vg.total_views), SUM(vg.total_unique_views) FROM Contests AS con JOIN Colleges AS col ON con.contest_id = col.contest_id JOIN Challenges AS cha ON cha.college_id = col.college_id LEFT JOIN (SELECT ss.challenge_id, SUM(ss.total_submissions) AS total_submissions, SUM(ss.total_accepted_submissions) AS total_accepted_submissions FROM  Submission_Stats AS ss GROUP BY ss.challenge_id) AS sg ON cha.challenge_id = sg.challenge_id LEFT JOIN (SELECT vs.challenge_id, SUM(vs.total_views) AS total_views, SUM(total_unique_views) AS total_unique_views FROM View_Stats AS vs GROUP BY vs.challenge_id) AS vg ON cha.challenge_id = vg.challenge_id GROUP BY con.contest_id, con.hacker_id, con.name HAVING SUM(sg.total_submissions)+       SUM(sg.total_accepted_submissions)+       SUM(vg.total_views)+       SUM(vg.total_unique_views) > 0 ORDER BY con.contest_id;

**Q:Content Leadership**

You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!

The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of  from your result.

**Answer**

SELECT con.contest_id, con.hacker_id, con.name, SUM(sg.total_submissions), SUM(sg.total_accepted_submissions),
SUM(vg.total_views), SUM(vg.total_unique_views) FROM Contests AS con JOIN Colleges AS col ON con.contest_id = col.contest_id
JOIN Challenges AS cha ON cha.college_id = col.college_id LEFT JOIN (SELECT ss.challenge_id, SUM(ss.total_submissions) AS total_submissions, SUM(ss.total_accepted_submissions) AS total_accepted_submissions FROM Submission_Stats AS ss GROUP BY ss.challenge_id) AS sg ON cha.challenge_id = sg.challenge_id LEFT JOIN (SELECT vs.challenge_id, SUM(vs.total_views) AS total_views, SUM(total_unique_views) AS total_unique_views FROM View_Stats AS vs GROUP BY vs.challenge_id) AS vg ON cha.challenge_id = vg.challenge_id GROUP BY con.contest_id, con.hacker_id, con.name HAVING SUM(sg.total_submissions)+  SUM(sg.total_accepted_submissions)+ SUM(vg.total_views)+ SUM(vg.total_unique_views) > 0 ORDER BY con.contest_id;
