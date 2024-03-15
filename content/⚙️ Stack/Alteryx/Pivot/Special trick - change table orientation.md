# Special trick - change table orientation

eg challenge 330

to change the table like this, we need to use both transpose and crosstab

[[Special trick - change table orientation/Untitled.png]]

we need to one more column (F1) because it will become the header in crosstab step

[[Special trick - change table orientation/Untitled 1.png]]

first transpose all other columns with F1 as key columns

[[Special trick - change table orientation/Untitled 2.png]]

then in crosstab step,

group by name so that it become row of column

specific the column headers and value as our value in the tables (aggregation doesn’t matter)

[[Special trick - change table orientation/Untitled 3.png]]
