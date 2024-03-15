# leetcode SQL50-

**[1070. Product Sales Analysis III](https://leetcode.com/problems/product-sales-analysis-iii/):** Double column filtering with IN keywords 

```sql
# Write your MySQL query statement below
select product_id ,year as first_year,quantity,price
from Sales
where (product_id,year) in (select product_id,min(year) from Sales group by 1);
```

**[1661. Average Time of Process per Machine](https://leetcode.com/problems/average-time-of-process-per-machine/):** special join condition

```sql
select A1.machine_id,round(avg(A2.timestamp -A1.timestamp),3) as processing_time from Activity A1
JOIN Activity A2 ON A1.machine_id = A2.machine_id
AND A1.process_id = A2.process_id
AND A1.activity_type = 'start'
AND A2.activity_type = 'end'
group by A1.machine_id
```

difficulty: **Product Price at a Given Date**

get 2nd largest

```
select max(salary) as SecondHighestSalary 
from employee
where salary < (select max(salary) from employee);
```

**[1484. Group Sold Products By The Date](https://leetcode.com/problems/group-sold-products-by-the-date/): row rolling up + string concatentation**