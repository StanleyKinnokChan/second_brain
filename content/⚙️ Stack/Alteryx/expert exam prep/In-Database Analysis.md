# In-Database Analysis

• Create new in-database connection strings
• Connect to SQL database tables
• Stream data into an in-database workflow
• Analyze data using in-database tools and appropriate SQL syntax
• Change data types and sort data in-database
• Create and update tables in the database

Note:

- you cannot change data type using the in-DB select tool. Cast statement is needed to change the data type.
- formular in-DB tool adapt the syntax of SQL; double quote refers to columns, single quote refer to string; use case when … then… else … end for condition
- order can be sorted in sample tool

Function

• GETDATE()
• CAST(xxxx as yyyyy)
• CONVERT()
• FORMAT()
• DATEDIFF()
• ISNULL()

**DATENAME function will return the character string-based date and time of a specified date whereas the DATEPART function will return an integer-based date and time of a specified date**

datediff(interval, ‘end date’, ‘start date’)

CAST(xxxx as nvarchar(100))

FORMAT(date, ‘mmmm dd,yyyy’)
