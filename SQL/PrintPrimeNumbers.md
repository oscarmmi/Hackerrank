![image](https://user-images.githubusercontent.com/23621801/158853140-63b38cbc-411d-4ade-b50b-0f098bff3aac.png)

Write a query to print all prime numbers less than or equal to 1000. Print your result on a single line, and use the ampersand (&) 
character as your separator (instead of a space).

For example, the output for all prime numbers <=10 would be:

![image](https://user-images.githubusercontent.com/23621801/158856105-02f1d295-6470-4544-b8b7-f951a473a275.png)


## Answer (MySQL)

```sql

SELECT 
GROUP_CONCAT(NUMB SEPARATOR '&')
FROM (
    SELECT 
    @num:=@num+1 as NUMB 
    FROM information_schema.tables t1,
    information_schema.tables t2,
    (SELECT @num:=1) tmp
) tempNum
WHERE NUMB<=1000 AND NOT EXISTS(
        SELECT 
        * 
        FROM (
            SELECT 
            @nu:=@nu+1 as NUMA 
            FROM information_schema.tables t1,
            information_schema.tables t2,
            (SELECT @nu:=1) tmp1
            LIMIT 1000
        ) tatata
        WHERE 
        FLOOR(NUMB/NUMA)=(NUMB/NUMA) 
        AND NUMA<(FLOOR(NUMB/2)+1) 
        AND NUMA>1
    )

```


