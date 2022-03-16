![image](https://user-images.githubusercontent.com/23621801/158702059-609132c8-ff9d-45f5-83b2-0c327e12e48d.png)

P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

![image](https://user-images.githubusercontent.com/23621801/158702087-a6e9c958-8b05-44cc-9204-4c8c486371fd.png)

Write a query to print the pattern P(20).

## Answer (MySQL)

```sql

set @number = 21;
select 
repeat('* ', @number := @number - 1) 
from information_schema.tables
where 
@number > 1

```


