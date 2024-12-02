
1. window function only work in the SELECT statement
2. use join or exist to filter the data based on another dateset
3. join condition is not only for the column being match, but also filter the source table (1607. Sellers With No Sales)
4. use 'true'/'false' or 1/0 represent boolean
5. when using CASE statement, WHEN statement have to be used in each conditional expression
6. When joining same table multiple times, add number into alias like R1, R2, R3....Then you can select the values using R1.col, R2.col, R3.col...
7. Pivoting is not supported by every database, cross join could be one of the solution
8. You can filter the group by result where the aggregation condition in inside the group (1511. Customer Order Frequency)
9. Don't forget alias of sub-query after FROM
10. Recursive CTE ([1270. All People Report to the Given Manager](https://leetcode.com/problems/all-people-report-to-the-given-manager/)) is not only useful for hierarchy data, it is also useful for row-generation

grouping sequential data by state

3 ways to exclude the set by groups (except, not exist and left join)