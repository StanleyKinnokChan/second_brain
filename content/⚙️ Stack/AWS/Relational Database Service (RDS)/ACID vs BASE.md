# ACID vs BASE

- two database transaction model

- CAP therom
    -

    [[ACID vs BASE/Untitled.png]]


[[ACID vs BASE/Untitled 1.png]]

**ACID= focus on Consistency**

- limited to the DB to scale
- most relationship DB use this rule
- RDS database

[[ACID vs BASE/Untitled 2.png]]

**BASE = focus on Availablility**

- rather than enforcing immediate consistency, base model noSQL DB ensure availability be spreading and replicating data across all the different codes of that DB
- best to do consistent but no guarantee, you need to design the application to query to data in a way that the consistency is secured (offload to applications)
- highly scalable and very fast
- noSQL style database, however some feature of dynamoDB can have some acid property

[[ACID vs BASE/Untitled 3.png]]
