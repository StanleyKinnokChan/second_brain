---
title: 
tags:
  - SQL
  - performance
---
  
  


1. **Clustering Index:**
    
    - A clustering index is a type of index in which the physical order of rows in the table is the same as the indexed order.
    - In other words, the rows of the table are physically stored on disk in the same order as the index key values.
    - Each table can have only one clustering index because it determines the physical order of the rows.
    - When a table has a clustering index, it means that the data is physically organized based on the clustering key. This can improve the performance of queries that use the clustering key in their conditions because it allows for faster retrieval of rows that are stored contiguously on disk.
    
1. **Non-Clustering Index:**
    
    - A non-clustering index, also known as a secondary index, is an index in which the order of rows on disk does not match the indexed order.
    - Unlike clustering indexes, tables can have multiple non-clustering indexes.
    - Non-clustering indexes are useful for speeding up queries that search for specific values in columns that are not the primary key or clustering key. 
    - typically implemented as B-trees. Process:
		- The search process begins at the root node of the index tree and traverses down the tree, following branches based on comparisons between the search key and the keys stored in each node.
		- At each level of the tree, the search narrows down the range of possible rows until it reaches leaf nodes or pointers to actual data rows.
    - They provide a quick way to locate rows based on the indexed column(s), but once the rows are located, additional I/O operations may be required to retrieve the actual data. This is because the index itself does not contain the entire row data but rather pointers or references to the corresponding rows in the table.