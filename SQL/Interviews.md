![image](https://user-images.githubusercontent.com/23621801/158689010-e9485083-bf4e-4c8e-9d16-545c6d75579f.png)

Samantha interviews many candidates from different colleges using coding challenges and contests. 
Write a query to print the contest_id, hacker_id, name, and the sums of total_submissions, total_accepted_submissions, 
total_views, and total_unique_views for each contest sorted by contest_id. 
Exclude the contest from the result if all four sums are 0.

### Note:
A specific contest can be used to screen candidates at more than one college, but each college only holds 1 screening contest.


## Input Format

The following tables hold interview data:

* Contests: The contest_id is the id of the contest, hacker_id is the id of the hacker who created the contest, and name is the name of the hacker.

![image](https://user-images.githubusercontent.com/23621801/158689404-ca655fc7-d951-4e63-8ccf-1861de15668d.png)

* Colleges: The college_id is the id of the college, and contest_id is the id of the contest that Samantha used to screen the candidates.

![image](https://user-images.githubusercontent.com/23621801/158689480-26edf295-b142-4a51-9280-8d0e24ca48f5.png)


* Challenges: The challenge_id is the id of the challenge that belongs to one of the contests whose contest_id Samantha forgot, 
and college_id is the id of the college where the challenge was given to candidates.

![image](https://user-images.githubusercontent.com/23621801/158689546-11e6c586-211a-4544-b18d-105066c8ad46.png)


* View_Stats: The challenge_id is the id of the challenge, total_views is the number of times the challenge was 
viewed by candidates, and total_unique_views is the number of times the challenge was viewed by unique candidates.

![image](https://user-images.githubusercontent.com/23621801/158689643-4e7ffb92-4422-4bd0-8e00-9feeee0672ee.png)


### Submission_Stats Table:

![image](https://user-images.githubusercontent.com/23621801/158696244-d9f4748b-5756-4da0-90c7-c60bf742ad79.png)

* Submission_Stats: The challenge_id is the id of the challenge, total_submissions is the number of submissions for the challenge, 
and total_accepted_submission is the number of submissions that achieved full scores.

![image](https://user-images.githubusercontent.com/23621801/158690034-8d9a161d-f271-44a8-8a05-54445880eafd.png)


## Sample Input

### Contests Table: 

![image](https://user-images.githubusercontent.com/23621801/158693996-444978f2-c2a6-40f2-b343-9d1a9619a78b.png)

### Colleges Table:

![image](https://user-images.githubusercontent.com/23621801/158695232-af0bd6e1-b938-4e1b-a6a1-84b37314e129.png)

### Challenges Table:

![image](https://user-images.githubusercontent.com/23621801/158695392-16087659-142a-426a-ab06-ac1ca4ed0cff.png)

### View_Stats Table:

![image](https://user-images.githubusercontent.com/23621801/158695465-71cd9d74-623e-49cf-8d88-3c8fcce1d3dd.png)

### Sample Output

![image](https://user-images.githubusercontent.com/23621801/158696462-4ec283d3-aaab-4be4-9fae-a30ee5d5fb67.png)


## Explanation

![image](https://user-images.githubusercontent.com/23621801/158696665-3ca56c31-123a-47cd-9e9f-631f6d5b33c2.png)


## Answer (MySQL)

```sql

SELECT
a.contest_id,
a.hacker_id,
a.name,
SUM(ab.total_submissions) as total_submissions,
SUM(ab.total_accepted_submissions) as total_accepted_submissions,
SUM(ab.total_views) as total_views,
SUM(ab.total_unique_views) as total_unique_views
FROM (
    SELECT
    aa.challenge_id,
    SUM(aa.total_submissions) as total_submissions,
    SUM(aa.total_accepted_submissions) as total_accepted_submissions,
    SUM(aa.total_views) as total_views,
    SUM(aa.total_unique_views) as total_unique_views
    FROM (
        SELECT
        da.challenge_id,
        da.total_submissions,
        da.total_accepted_submissions,
        0 as total_views,
        0 as total_unique_views
        FROM Submission_Stats da
        UNION ALL
        SELECT
        ea.challenge_id,
        0 AS total_submissions,
        0 AS total_accepted_submissions,
        ea.total_views,
        ea.total_unique_views
        FROM View_Stats ea    
    ) aa
    GROUP BY aa.challenge_id    
) ab
JOIN Challenges c ON(c.challenge_id=ab.challenge_id)
JOIN Colleges d ON(d.college_id=c.college_id)
JOIN Contests a on(a.contest_id=d.contest_id)
GROUP BY a.contest_id, a.hacker_id, a.name
HAVING (total_submissions+total_accepted_submissions+total_views+total_unique_views)>0
ORDER BY a.contest_id

```







