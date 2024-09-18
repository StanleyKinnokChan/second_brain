---
title: 
tags:
  - Database
---
ACID is a set of properties of database transactions intended to guarantee data validity despite errors, power failures, and other mishaps

==**Atomicity**== is about all-or-nothing. Either the entire statement is executed, or none of it is executed

==**Consistency**== ensures that a transaction only brings the database from one valid state to another, abiding by all predefined rules (constraints, triggers, etc.) such as data types, relationships (foreign keys), and uniqueness constraints.

==**Isolation**== means ensures that the concurrent transactions don't interfere with or affect one another, if multiple users are reading and writing from the same table all at once

==**Durability**== guarantees that changes to your data made by successfully executed transactions will be saved, even in the event of system failure