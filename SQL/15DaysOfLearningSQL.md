## 15 Days of Learning SQL

![image](https://user-images.githubusercontent.com/23621801/160199344-28ac3e53-9017-47b3-a0cf-45ee3196bdc8.png)

Julia conducted a 15 days of learning SQL contest. The start date of the contest was March 01, 2016 and the end date was March 15, 2016.

Write a query to print total number of unique hackers who made at least 1 submission each day (starting on the first day of the contest), 
and find the hacker_id and name of the hacker who made maximum number of submissions each day. If more than one such hacker has a maximum number 
of submissions, print the lowest hacker_id. The query should print this information for each day of the contest, sorted by the date.

## Input Format

The following tables hold contest data:

* Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.

![image](https://user-images.githubusercontent.com/23621801/160196563-0b8e7db5-78d4-4dfd-9ab1-8ef3c89a3696.png)

* Submissions: The submission_date is the date of the submission, submission_id is the id 
of the submission, hacker_id is the id of the hacker who made the submission, and score is the score of the 
submission. 

![image](https://user-images.githubusercontent.com/23621801/160197054-fff0ba09-09bf-4cff-9cd1-57b9fbc9d977.png)

## Sample Input

For the following sample input, assume that the end date of the contest was March 06, 2016.

### Hackers Table: 

![image](https://user-images.githubusercontent.com/23621801/160197112-8da741c7-504d-42ef-b117-9ac0bb8d8669.png)

### Submissions Table:

![image](https://user-images.githubusercontent.com/23621801/160197970-98b34ebe-930d-4a77-b572-61a68c4c1e0e.png)

## Sample Output

![image](https://user-images.githubusercontent.com/23621801/160198002-dd91b7eb-9e17-4c66-b364-118415bd002b.png)


## Explanation


On March 03, 2016 hackers 20703, 36396 and 79722 made submissions. 
Now 20703 and 79722 were the only ones, so there are 2 unique hackers who made at least one submission each day. 
As each hacker made one submission so 20703 is considered to be the hacker who made maximum number of submissions 
on this day. The name of the hacker is Angela.

On March 04, 2016 hackers 20703, 44065, 53473, and 79722 made submissions. 
Now 20703 and 79722 only submitted each day, so there are 2 unique hackers who made at least one submission 
each day. 
As each hacker made one submission so 20703 is considered to be the hacker who made maximum number of submissions on this day. 
The name of the hacker is Angela.

On March 05, 2016 hackers 20703, 36396, 38289 and 62529 made submissions. Now 20703 only submitted each day, so there is only 1 
unique hacker who made at least one submission each day. 36396 made 2 submissions and name of the hacker is Frank.

On March 06, 2016 only 20703 made submission, so there is only 1 unique hacker who made at least one submission each day. 
20703 made 1 submission and name of the hacker is Angela.


## Answer (MySQL)

```sql

SELECT
SUBMISSION_DATE,
       (
SELECT
Count(DISTINCT hacker_id) as no_of_unique_hacker_id
FROM submissions S2
        WHERE  
S2.submission_date = S1.submission_date
        AND (
SELECT
Count(DISTINCT S3.submission_date)
            FROM   submissions S3
            WHERE  
S3.hacker_id = S2.hacker_id
            AND S3.submission_date < S1.submission_date
   ) = Datediff(S1.submission_date, '2016-03-01')
       ) AS NO_OF_UNIQUE_HACKERS,
       (
SELECT
hacker_id
FROM submissions S2
        WHERE  
S2.submission_date = S1.submission_date
        GROUP  BY hacker_id
        ORDER  BY Count(submission_id) DESC, hacker_id ASC LIMIT  1
       ) AS MAX_SUB_HACKER_ID,
       (
SELECT
name
FROM hackers
        WHERE  hacker_id = MAX_SUB_HACKER_ID
       ) AS NAME
FROM   (
SELECT DISTINCT
submission_date
FROM submissions
) S1
GROUP BY submission_date;


```
