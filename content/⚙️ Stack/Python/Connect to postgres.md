---
title: 
tags:
  - python
  - Template
---
Using psycopg
```
import psycopg

#establishing the connection
conn = psycopg2.connect(
   database="postgres", user='postgres', password='mysecretpassword', host='localhost', port= '5432'
)

#Creating a cursor object using the cursor() method
cursor = conn.cursor()


#Executing an MYSQL function using the execute() method
cursor.execute("select version()")

# Fetch a single row using fetchone() method.
data = cursor.fetchone()

#Closing the connection
conn.close()

```


Using sqlalchemy
```
from sqlalchemy import create_engine    

engine = create_engine('postgresql+psycopg2://postgres:mysecretpassword@localhost:5432/postgres')

df.to_sql('test_table', engine, if_exists='append', index=False)
```