---
title: 
tags:
---
Step 1. In the Airflow UI, expand the admin tab and choose connection. 
Step 2. Enter the connection details
	> if we are using docker as container in Window or Mac, using `localhost` as host name won't work. Instead we need to use `host.docker.local` ([a special DNS](https://docs.docker.com/desktop/networking/))
Step 3. In the DAG file, import the target DB operator and state the conn_id previously 

entered
```
# example:
with DAG(

    dag_id='dag_with_postgres_operator_v03',

    default_args=default_args,

    start_date=datetime(2024, 3, 17),

    schedule_interval='0 0 * * *'

) as dag:

    task1 = PostgresOperator(

        task_id='create_postgres_table',

        postgres_conn_id='postgres_localhost',

        sql="""

            create table if not exists dag_runs (

                dt date,

                dag_id character varying,

                primary key (dt, dag_id)

            )

        """

    )
```