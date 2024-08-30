
## Conditional Branch
We can configure airflow to run the branch that pass the condition and skip the ones which failed
Just setup a function returning the task and use branch operator to add the condition to the DAG

```
def _branch(ti):
    value = ti.xcom_pull(key='my_key', task_ids='t2')
    if (value==42):
        return 't2'
    return 't3'

...

	branch = BranchPythonOperator(
        task_id='branch',
        python_callable=_branch
    )
...


  t1 >> branch >> [t2,t3] >> t4
  
```


However, any task skpped will lead to the skip of the downstream. 
In the case above, skipping t3 will lead to the skipping t4, even t2 run successfully.
As a result, we need **trigger rule**.

## Trigger Rule

1. all_success: run if all success
2. all_failed: run if all fail
3. all_done: run regardless of the upstream state
4. one_sucess: run if any one success without waiting other tasks
5. one_fail: run if any one fail without waiting other tasks
6. none-failed: run if all success or skipped
7. none-skipped: runs if no direct upstream task is in a skipped state.
8. none_failed_min_one_success: run at least one success, if there are other skipped tasks
```
#just add trigger_rule to the DAG

    t4 = BashOperator(
        task_id='t4',
        bash_command="echo 'task 4'",
        trigger_rule='none_failed_min_one_success'
    )
```
