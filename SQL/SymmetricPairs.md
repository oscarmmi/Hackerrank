![image](https://user-images.githubusercontent.com/23621801/158420139-6eed9900-4b57-4be0-90c6-910444d09cbd.png)

You are given a table, Functions, containing two columns: X and Y.

![image](https://user-images.githubusercontent.com/23621801/158420221-ac57298e-c8b5-4eda-96a7-a8bdc7b4414e.png)

Two pairs (X1, Y1) and (X2, Y2) are said to be symmetric pairs if X1 = Y2 and X2 = Y1.

Write a query to output all such symmetric pairs in ascending order by the value of X. List the rows such that X1 ≤ Y1.

## Sample Input

![image](https://user-images.githubusercontent.com/23621801/158420340-1888115f-d9e4-45b3-94c8-82a19cbe8302.png)

## Sample Output

![image](https://user-images.githubusercontent.com/23621801/158420397-3cea55f7-415d-4bfe-9c72-68ca51dc3b90.png)

```sql

SELECT 
aaa.*
FROM (
    SELECT 
    a.X, 
    a.Y
    FROM Functions a 
    WHERE 
    a.X = a.Y
    AND (
        SELECT 
        count(b.X)
        FROM Functions b 
        WHERE 
        b.Y=a.X
        and b.X=a.Y 
    ) > 1 
    UNION 
    SELECT 
    aa.X, 
    aa.Y
    FROM Functions aa 
    WHERE 
    EXISTS (
        SELECT 
        1
        FROM Functions ab 
        WHERE 
        ab.Y=aa.X 
        AND ab.X=aa.Y 
        AND aa.X<ab.X
    )
) aaa 
ORDER BY aaa.X ASC 

```
