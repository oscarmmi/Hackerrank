
![image](https://user-images.githubusercontent.com/23621801/158703967-f55561ad-d333-4126-b691-de64429f46e7.png)

P(R) represents a pattern drawn by Julia in R rows. The following pattern represents P(5):

![image](https://user-images.githubusercontent.com/23621801/158704020-e0703055-f381-486a-984a-b9a9d61c147d.png)

Write a query to print the pattern P(20).

```sql

set @number = 0;
select repeat('* ', @number := @number + 1) 
from information_schema.tables
where @number < 20

```
