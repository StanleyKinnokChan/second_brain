---
title: 
tags:
---
Normalization is the process of structuring a database to improve data integrity and reduce redundancy.

First Normal Form (1NF):
- requires a primary key
- each column must be atomic

Second Normal Form (2NF):
- 1NF
- all non-prime attributes belongs to entire candidate key
- = any non-prime attributes is dependent on the whole information in the candidate key
- = removal of partial dependencies

Third Normal Form (3NF):
- 2NF
- Ensure each column to directly related to primary key, but not others non-prime attribute
- = removal of transitive dependency on another key

