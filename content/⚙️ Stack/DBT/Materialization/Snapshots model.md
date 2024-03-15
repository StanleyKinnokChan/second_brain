# Snapshots model

snapshots capture the old table + changes and create a new table using the name in {% snapshot <snapshot_name> %} and schema specified in {{ config() }}. 

let say the old table has 3 rows and 1 row is changed. The new snapshot table will have 4 rows.

strategy:

1. timestamp: compare the timestamp column with time when **dbt snapshot** command is run.
2. Check: specify the columns

1st run: create the table same as the ref

2st run: table + change1

3rd run: table + change1 + changes2