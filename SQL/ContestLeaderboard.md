![image](https://user-images.githubusercontent.com/23621801/158268602-b6c00755-a399-4e26-a077-a3b3c9c8de05.png)


You did such a great job helping Julia with her last coding contest challenge that she wants you to work on this one, too!

The total score of a hacker is the sum of their maximum scores for all of the challenges. Write a query to print the hacker_id, name, and total score of the hackers ordered by the descending score. If more than one hacker achieved the same total score, then sort the result by ascending hacker_id. Exclude all hackers with a total score of 0 from your result.


## Input Format

The following tables contain contest data:

* Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker.

![image](https://user-images.githubusercontent.com/23621801/158267269-7f08495a-b14b-4d4e-a979-50639c36cd3f.png)

* Submissions: The submission_id is the id of the submission, hacker_id is the id of the hacker who made the submission, challenge_id is the id of the challenge for which the submission belongs to, and score is the score of the submission.

![image](https://user-images.githubusercontent.com/23621801/158267352-f1d05e7b-5cfc-47b2-b4ef-980d9cd56ac5.png)

## Sample Input

### Hackers Table: 

![image](https://user-images.githubusercontent.com/23621801/158267435-dbc71bf7-de68-43f5-a5a2-8a25f1e13a73.png)

### Submissions Table:

![image](https://user-images.githubusercontent.com/23621801/158268311-92dac560-6a22-4caa-b1bd-8bdfbdb61255.png)

## Sample Output

![image](https://user-images.githubusercontent.com/23621801/158268363-fab97caf-ec8b-4aec-a8da-84f92cd32b55.png)

## Explanation

![image](https://user-images.githubusercontent.com/23621801/158268395-f546e1a9-9d9e-49f2-b768-f8c95848c9a0.png)

## Answer (MySQL)

```sql
SELECT 
a.hacker_id, 
a.name, 
COALESCE(SUM(b.max_score_by_challenge), 0) AS total_score
FROM Hackers a 
LEFT JOIN (
    SELECT
    aa.hacker_id, 
    aa.challenge_id,
    MAX(aa.score) AS max_score_by_challenge
    FROM Submissions aa 
    GROUP BY aa.hacker_id, aa.challenge_id
) b ON(a.hacker_id=b.hacker_id) 
GROUP BY a.hacker_id, a.name
HAVING total_score>0
ORDER BY total_score DESC, a.hacker_id ASC 
```
