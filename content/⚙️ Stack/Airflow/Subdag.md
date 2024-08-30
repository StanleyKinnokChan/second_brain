---
title: 
tags:
---
1. apart from the main dag, open a subdag folder
2. inside the folder, create subdag_downloads.py
3. import bash operator as the task that group together
4. write a function to wrap the dag, with parent & child dag parameter
5. import subdagoperator into main dag

e.g. 
```
def subdag_downloads(parenet_dag_id, child_dag_id, args):

  

    with DAG(f"{parenet_dag_id,child_dag_id}",

             start_date=args['start_date'],

             schedule_interval=args['schedule_interval'],

             catchup=args['catchup']      

             ) as dag:
             

        download_a = BashOperator(

            task_id = 'download_a',

            bash_command='sleep 10'

        )

  

        download_b = BashOperator(

            task_id = 'download_a',

            bash_command='sleep 10'

        )

  

        download_c = BashOperator(

            task_id = 'download_a',

            bash_command='sleep 10'

        )

  

    return dag
```

6. create an args dict for the subdag parent within the main dag, which inherent the parameter from the main dag
```
with DAG('group_dag', start_date=datetime(2022, 1, 1),
    schedule_interval='@daily', catchup=False) as dag:

    args = {'start_date':dag.start_date, 'schedule_interval': dag.schedule_interval, 'catchup': dag.catchup}
    
    .....
    
```

7. replace the grouped tasks with SubDagOperator, with all 3 neccery arguments

```
with DAG('group_dag', start_date=datetime(2022, 1, 1),

    schedule_interval='@daily', catchup=False) as dag:

  

    args = {'start_date':dag.start_date, 'schedule_interval': dag.schedule_interval, 'catchup': dag.catchup}

  

    downloads = SubDagOperator(

        task_id='downloads',

        subdag=subdag_downloads(dag.dag_id,'downloads',args)

    )
```

8. import the fuction from the module you created previous
```
from subdags.subdag_downloads import subdag_downaloads
```

9. using new object to replace the task order
```
    downloads >> check_files >> [transform_a, transform_b, transform_c]
```