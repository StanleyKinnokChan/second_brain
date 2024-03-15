# Type of database

**dynamoDB**

- wide column store, fast and super-scalable
- but not able to use relational operation like SQL

**document**

- like extention of key and value
- good for nice for orders/ contacts style data, whole documents/ deep attribute interactions

**row-based database** (eg mysql)

- most of the traditional database
- scan all rows for a specific row
- idea if need operating with rows adding, updating, deleting (stock, transaction)
- online transaction processing (OLTP)

**column database** (redshift)

- store data based on column
- normally shift from the row-based database, for analysis
- Online analytical processing (OLAP)

[[Type of database/Untitled.png]]

**Graph database**

- multiple nodes inside database, each has key and value
- relationship between nodes (edge)
- good for highly complex relationship between node (social media/ HR data)

    [[Type of database/Untitled 1.png]]
