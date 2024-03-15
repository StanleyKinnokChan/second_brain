# Local & Global Secondary Indexes

- query is the most efficient operation but only 1PK and optionally SK values
- indexes are alternative views on table data
- can choose some/ all attributes to create the view
    - project attributes via - ALL, KEYS_ONLY & INCLUDE
- queries on attributes not projected are expensive (will do extra work for you in the backend)

**Local Secondary Indexes**

[[Local & Global Secondary Indexes/Untitled.png]]

- create a view using different SK (choosing an attributes as an alternative sort key) and same PK
- **must be created with a base table,** cannot be added after base table has been created
- **limit of 5** per table
- **shares the RCU & WCU** with the table
- **both consistency model** are fine

**Global Secondary Indexes**

[[Local & Global Secondary Indexes/Untitled 1.png]]

- create a view using different PK & SK
- **can be created at any time**
- **limit of 20** per base table
- have their **own RCU & WCU**
- **always need to be eventually consistent**
