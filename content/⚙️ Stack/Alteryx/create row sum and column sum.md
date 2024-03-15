# create row sum and column sum

source: weekly challenge 324

### row and column total at once

1. transpose the data (row identifier is need)
2. then reshape back the original table using crosstab with aggregation method, total row and total column
3. use dynamic rename to remove the prefix of the column name, which is the aggregation method (eg Sum_colname)

### row with subtotal

1. classify the row
2. use summerize to sum of row, group by classification
3. union to original table
