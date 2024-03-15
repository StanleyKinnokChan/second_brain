# Materialization

DBT wrap the model queries with DDL or DML and create view or table in the Datawarehouse. 

**Ephemeral model**:  take the select statement, it imports the statement as CTEs as downstream model, won’t create anything in the data warehosue

[**Incremental model**](Materialization%20a8318aa4a4aa4461b50292c26d6b571b/Incremental%20model%207cd17d506bca4936868b6d87f59a15c5.md)

**:** Look at the table underlying the view and take the data that is new into an existing data. 

[**Snapshots model**](Materialization%20a8318aa4a4aa4461b50292c26d6b571b/Snapshots%20model%20ea42d14fa5f04a69b99573f7a49d445e.md)

 ****Look at underlying data and find out any records that have changed, bring into  an existing table