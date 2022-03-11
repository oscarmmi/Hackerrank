# Hackerrank

![image](https://user-images.githubusercontent.com/23621801/157910858-72797917-f64a-4fdc-a42d-25f702962484.png)

Julia asked her students to create some coding challenges. Write a query to print the hacker_id, name, and the total number of challenges created by each student. Sort your results by the total number of challenges in descending order. If more than one student created the same number of challenges, then sort the result by hacker_id. If more than one student created the same number of challenges and the count is less than the maximum number of challenges created, then exclude those students from the result.

### Input Format

The following tables contain challenge data:

* Hackers: The hacker_id is the id of the hacker, and name is the name of the hacker. 

![image](https://user-images.githubusercontent.com/23621801/157917278-9e739c40-bce2-469e-88ee-20f40256aa6f.png)


* Challenges: The challenge_id is the id of the challenge, and hacker_id is the id of the student who created the challenge. 

![image](https://user-images.githubusercontent.com/23621801/157930914-05990901-3f0b-489f-82aa-a4d6d13249d6.png)


## Sample Input 0

### Hackers Table:  

![image](https://user-images.githubusercontent.com/23621801/157932049-aba7eecd-dbef-4115-94b4-418d68c2df21.png)


### Challenges Table: 

![image](https://user-images.githubusercontent.com/23621801/157932277-cb0beb5c-64e0-438f-9480-bad738b9039c.png)

## Sample Output 0

21283 Angela 6
88255 Patrick 5
96196 Lisa 1
Sample Input 1

![image](https://user-images.githubusercontent.com/23621801/157932332-d4d2268c-8be0-4892-af83-26605e006b0b.png)

## Hackers Table:  

![image](https://user-images.githubusercontent.com/23621801/157932491-23044fb2-4ebf-4516-879d-efa28be36e6e.png)

## Challenges Table: 

![image](https://user-images.githubusercontent.com/23621801/157932608-0a74aac4-672b-473c-a5ac-96a4de2cbfc0.png)

## Sample Output 1

12299 Rose 6
34856 Angela 6
79345 Frank 4
80491 Patrick 3
81041 Lisa 1

![image](https://user-images.githubusercontent.com/23621801/157932865-3d0570d7-9ef4-4384-a0a5-638f6ebde7a0.png)


## Explanation

For Sample Case 0, we can get the following details:

![image](https://user-images.githubusercontent.com/23621801/157936692-f49c45c6-f70f-42a4-923a-0b605bd3a32d.png)

Students  and  both created  challenges, but the maximum number of challenges created is  so these students are excluded from the result.

For Sample Case 1, we can get the following details:

![image](https://user-images.githubusercontent.com/23621801/157936859-efb04a71-8b5c-465b-8ed2-e577924bbc49.png)

Students  and  both created  challenges. Because  is the maximum number of challenges created, these students are included in the result.



## Answer (MySQL)


SELECT 
aa.hacker_id, 
aa.name, 
COUNT(ab.challenge_id) AS counter_challenges
FROM Hackers aa 
JOIN Challenges ab ON(ab.hacker_id = aa.hacker_id)
GROUP BY aa.hacker_id, aa.name
HAVING 
counter_challenges NOT IN(
    SELECT 
    f.number_challenges
    FROM (
        SELECT 
        e.number_challenges, 
        COUNT(e.hacker_id) AS num_hackers
        FROM (
            SELECT 
            b.hacker_id, 
            COUNT(b.challenge_id) AS number_challenges
            FROM  Challenges b 
            GROUP BY b.hacker_id 
            HAVING 
            number_challenges<(
                SELECT 
                MAX(d.contador_challenges) AS max_challenges 
                FROM (
                    SELECT 
                    c.hacker_id, 
                    COUNT(c.challenge_id) AS contador_challenges
                    FROM Challenges c 
                    GROUP BY c.hacker_id
                ) d
            )
        ) e 
        GROUP BY e.number_challenges
        HAVING num_hackers>1
    ) f
) 
ORDER BY counter_challenges DESC, aa.hacker_id ASC 



