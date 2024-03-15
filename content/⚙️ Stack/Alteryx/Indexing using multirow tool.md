# Indexing using multirow tool

add repeating sequence ID (1,2,3,4,5,1,2,3,4,5)

- start at 1 every time when the cell in [flag] column has the string value ‘name’
if [Flag]== "Name" then [Row-1:ID]+1 else [Row-1:ID] endif
- self-referencing
if [Row-1:ID]==3 or [Row-1:ID]==0 then 1 else [Row-1:ID]+1 endif
