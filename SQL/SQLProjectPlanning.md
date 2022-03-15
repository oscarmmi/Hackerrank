![image](https://user-images.githubusercontent.com/23621801/158387937-aefc8df1-00d2-4d7d-9af9-c2053f3792e0.png)


You are given a table, Projects, containing three columns: Task_ID, Start_Date and End_Date. 
It is guaranteed that the difference between the End_Date and the Start_Date is equal to 1 day for each row in the table.

![image](https://user-images.githubusercontent.com/23621801/158387270-edca7c55-349c-4132-849a-03c6fc217eee.png)

If the End_Date of the tasks are consecutive, then they are part of the same project. Samantha is interested in finding the total number of different projects completed.

Write a query to output the start and end dates of projects listed by the number of days it took to complete the project in ascending order. 
If there is more than one project that have the same number of completion days, then order by the start date of the project.


## Sample Input

![image](https://user-images.githubusercontent.com/23621801/158387404-54a2f465-8f4d-4f0d-98bd-070a3af73690.png)


## Sample Output

![image](https://user-images.githubusercontent.com/23621801/158387497-8b934772-10d8-4442-bfbd-e3aa35f2af4e.png)

## Explanation

The example describes following four projects:

* Project 1: Tasks 1, 2 and 3 are completed on consecutive days, so these are part of the project. 
Thus start date of project is 2015-10-01 and end date is 2015-10-04, so it took 3 days to complete the project.

* Project 2: Tasks 4 and 5 are completed on consecutive days, so these are part of the project. 
Thus, the start date of project is 2015-10-13 and end date is 2015-10-15, so it took 2 days to complete the project.

* Project 3: Only task 6 is part of the project. Thus, the start date of project is 2015-10-28 and end date is 2015-10-29, 
so it took 1 day to complete the project.

* Project 4: Only task 7 is part of the project. Thus, the start date of project is 2015-10-30 
and end date is 2015-10-31, so it took 1 day to complete the project.


### Answer (MySQL)

```sql
SELECT 
Start_Date, 
min(End_Date)
FROM (
    SELECT 
    Start_Date 
    FROM Projects 
    WHERE 
    Start_Date NOT IN (
        SELECT 
        End_Date 
        FROM Projects
    )
) a ,
 (
     SELECT 
     End_Date 
     FROM Projects 
     WHERE 
     End_Date NOT IN (
         SELECT 
         Start_Date 
         FROM Projects
     )
 ) b
WHERE Start_Date < End_Date
GROUP BY Start_Date
ORDER BY DATEDIFF(min(End_Date), Start_Date) ASC, Start_Date ASC;
```
