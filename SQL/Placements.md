
![image](https://user-images.githubusercontent.com/23621801/158639477-3713ce4c-c1fd-4680-9d78-2cfb5c61d2d9.png)


You are given three tables: Students, Friends and Packages. Students contains two columns: ID and Name. Friends contains two columns: ID and Friend_ID (ID of the ONLY best friend). Packages contains two columns: ID and Salary (offered salary in $ thousands per month).

![image](https://user-images.githubusercontent.com/23621801/158639544-5fec2a94-0257-4720-9cce-eb76718e29d5.png)

![image](https://user-images.githubusercontent.com/23621801/158639622-91486d52-a4e1-4fd9-b106-7211ac1682f7.png)

Write a query to output the names of those students whose best friends got offered a higher salary than them. Names must be ordered by the salary amount offered to the best friends. It is guaranteed that no two students got same salary offer.

## Sample Input

![image](https://user-images.githubusercontent.com/23621801/158640284-d9c62c16-b33f-40d6-b1dc-d2cf2d45fb46.png)

![image](https://user-images.githubusercontent.com/23621801/158640397-1f603052-492e-4ea6-b7d7-9d8829118239.png)

## Sample Output

![image](https://user-images.githubusercontent.com/23621801/158640499-cb4218cb-08b7-4339-aa42-759a8574680d.png)

## Explanation

See the following table:

![image](https://user-images.githubusercontent.com/23621801/158641074-2b419efc-8717-48ff-a7b5-bac4d4b356c3.png)

Now,

* Samantha's best friend got offered a higher salary than her at 11.55
* Julia's best friend got offered a higher salary than her at 12.12
* Scarlet's best friend got offered a higher salary than her at 15.2
* Ashley's best friend did NOT get offered a higher salary than her

The name output, when ordered by the salary offered to their friends, will be:

* Samantha
* Julia
* Scarlet



## Answer

```sql
SELECT 
a.Name
FROM Students a 
JOIN Packages b ON(b.ID=a.ID) 
JOIN (
    SELECT
    aa.ID, 
    MAX(ab.Salary) AS Salary_Friend
    FROM Friends aa 
    JOIN Packages ab ON(ab.ID=aa.Friend_ID)
    GROUP BY aa.ID
) c ON(c.ID=a.ID) 
WHERE 
c.Salary_Friend>b.Salary
ORDER BY c.Salary_Friend ASC 
```

