
X-com stands for cross-communication. It is used for sharing data/ parameter across the tasks. 
For example, task 1 can create a file list, and from that task 2 read the data from these list.
It is not meant to be sharing large amount of data. 

There are two ways to push the values to x-com:

1. return from function
	If a DAG function return a value, it automatically push to x-com with 'return' as key_id. 
```
def _t1():
	return 10
```

2. specify the parameter and xcom_push
```
def _t1(ti):
	ti.xcom_push(key='my_key', value=42)
```

To get the value,  specify the parameter and use xcom_pull:
```
def _t2(ti):
	ti.xcom_pull(key='my_key', task_ids='t1')
```