# SQL

- Order of operation

    [[order of SQL queries.bmp]]

- Set Operator
    - left join

        ```sql
        # keep all key records  in left, join the key records in right that only match the left
        SELECT column_name(s)
        FROM t1
        LEFT JOIN t2
        ON t1.key = t2.key;
        ```

    - inner join

        ```sql
        # join the key records only found in both left and right
        SELECT column_name(s)
        FROM t1
        INNER JOIN t2
        ON t1.key = t2.key;
        ```

    - FULL OUTER JOIN/ FULL JOIN (same)

        ```sql
        #keep all the keys from both table, if a key in a table does not appear in other table, return the fields as NA
        SELECT column_name(s) FROM t1
        UNION
        SELECT column_name(s) FROM t2;
        ```

    - Cross join

        ```sql
        #join each record in a table with all the records in other table
        SELECT column_name(s) FROM t1
        CROSS JOIN
        SELECT column_name(s) FROM t2;
        ```

    - Union (remove duplicates)/ Union all (not  to remove duplicates) (Addition)

        ```sql
        #combine records in two table, data types of each column has to be the same and ordered
        SELECT column_name(s) FROM t1
        UNION
        SELECT column_name(s) FROM t2;
        ```

    - Except (Substraction)

        ```sql
        #Substract T2 from T1 (= T1 without T2)
        SELECT column_name FROM t1
        EXCEPT
        SELECT column_name FROM t2;
        ```

- Conditions
    - Exists

        ```sql
        SELECT column_name(s)
        FROM T1
        WHERE EXISTS
        (SELECT column_name FROM T2 WHERE conditions);

        --normally the conditions would be T1.column=T2.column to see if T1 records appear in T2 with other specific conditions in T2
        ```

    - Any

        ```sql
        SELECT column_name(s)
        FROM T1
        WHERE c1 operator ANY
          (SELECT c2
          FROM T2
          WHERE condition);

        --filter out the records from T1 by evaluating the value in T1.C1 >/</= any single value in T2.C2
        ```

    - All

        ```sql
        SELECT column_name(s)
        FROM table_name
        WHERE column_name operator ALL
          (SELECT column_name
          FROM table_name
          WHERE condition);

        --filter out the records from T1 by evaluating the value in T1.C1 >/</= All value in T2.C2
        -- using ALL with "=" operator is meaningless. No value can equal >1 different values. Values in T2.C2 have to be all the same in order to have records.
        ```

- Manipulation (DML; records)
    - Insert

        ```sql
        #manual enter
        INSERT INTO TableName (col1, col2, col3)
        VALUES ('val1a', 'val1b', 'val1c')
        VALUES ('val2a', 'val2b', 'val2c')
        ....;

        #from another table
        INSERT INTO table2 (column1, column2, column3, ...)
        SELECT column1, column2, column3, ...
        FROM table1
        WHERE condition;
        ```

    - Update

        ```sql
        UPDATE tableName
        SET column1=value1, column2=value2,...
        WHERE filterColumn=filterValue;
        ```

    - Delete

        ```sql
        --delete existing records
        DELETE FROM table_name WHERE condition;
        ```

- Description (DDL; schema, structure & type)
    - Create Table

        ```sql
        CREATE TABLE [IF NOT EXISTS] table_name (
           column1 datatype(length) column_contraint,
           column2 datatype(length) column_contraint,
           column3 datatype(length) column_contraint,
           table_constraints
        );
        ```

        - Data Type
        - Contraint
            - [NOT NULL](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-not-null-constraint/) – ensures that values in a column cannot be `NULL`.
            - [UNIQUE](https://www.postgresqltutorial.com/postgresql-unique-constraint/) – ensures the values in a column unique across the rows within the same table.
            - [PRIMARY KEY](https://www.postgresqltutorial.com/postgresql-tutorial/postgresql-primary-key/) – a primary key column uniquely identify rows in a table. A table can
            have one and only one primary key. The primary key constraint allows you to define the primary key of a table.
            - [CHECK](https://www.postgresqltutorial.com/postgresql-check-constraint/) – a `CHECK` constraint ensures the data must satisfy a boolean expression.
            - [FOREIGN KEY](https://www.postgresqltutorial.com/postgresql-foreign-key/) – ensures values in a column or a group of columns from a table exists
            in a column or group of columns in another table. Unlike the primary
            key, a table can have many foreign keys.``
            - SET DEFAULT xxxxx
    - Duplicate Table

        ```sql
        CREATE TABLE T2 AS SELECT * FROM T1;
        ```

    - Drop Table

        ```sql
        DROP TABLE table_name;
        ```

    - Alter
        - add a column

            ```sql
            ALTER TABLE table_name
            ADD column_name datatype;
            ```

        - drop a column

            ```sql
            ALTER TABLE table_name
            DROP COLUMN column_name;
            ```

        - change data type of a column

            ```sql
            ALTER TABLE table_name
            ALTER COLUMN column_name datatype;
            ```

        - add constraint to a column

            ```sql
            ALTER TABLE Persons
            ADD CONSTRAINT PK_Person PRIMARY KEY (ID,LastName);
            ```

        - rename a table

            ```sql
            ALTER TABLE table_name
            RENAME TO new_table_name
            ```

    - TRUNCATE (delete all row)

        ```sql
        TRUNCATE TABLE T1;
        ```


window function

- cannot be filter

- **Concept**
    - different between table and view in SQL

        A table and a view are two types of objects in a SQL database. Both are used to store and manage data, but they have some key differences:

        1. **Storage:** A table is a physical object in a database that stores data as rows and columns. The data in a table is stored on a disk and can take up physical space. On the other hand, a view is a virtual table that does not take up physical space, and its data is derived from one or more underlying tables.
        2. **Updatability:** A table can be updated directly, meaning that data can be inserted, updated, or deleted from the table. A view, on the other hand, is read-only and cannot be directly updated. Any changes to the data must be made to the underlying tables.
        3. **Security:** A view can be used to control access to sensitive data by hiding some columns or restricting access to certain rows. This can be useful for implementing row-level security in a database.
        4. **Performance:** Queries against a table can be more performant than queries against a view because the data is stored in a structured format. Queries against a view can be slower because they may involve additional processing to derive the data from the underlying tables.
        5. **Maintenance:** Tables can be altered or dropped, whereas views can only be altered, not dropped. When a table is altered, the changes are reflected in any associated views, whereas changes to a view do not affect the underlying tables.

        In general, a table is used to store data in a database, whereas a view is used to present a subset of the data or to present the data in a specific format. Views can be useful for simplifying the structure of a database, improving performance, and enhancing security.

    - 5 commandments SQL
        - one clause/ field/keyword per line
        - title, upper, lower case consistent
        - meaningful alias
        - use indentation and whitespace
        - write comments

[[performance]]

[[special ]]
