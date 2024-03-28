
Airflow only works in Linux-like environments (Linux/MacOS). You inevitably have to use WSL. When 

**Step1:** [[Create & activate python venv &package]]

**Step2:** Install airflow using pip ([official website](https://airflow.apache.org/docs/apache-airflow/stable/installation/installing-from-pypi.html)). The constraints should match the python version, which can be checked via `python --version`
```
pip install "apache-airflow[celery]==2.8.3" --constraint "https://raw.githubusercontent.com/apache/airflow/constraints-2.8.3/constraints-3.8.txt"
```

**Step3:** At the project folder, set the current directory as the airflow home environment variable
```
//widnow
set AIRFLOW_HOME=.


//widnow
export AIRFLOW_HOME=.
```

**Step4:** initialize the airflow DB, which create a SQLite DB, log folders and some configuration files. From now on, you have to swtich to WSL for using `airflow` command.
```
airflow db init
```

Step5: Start airflow webserver (8080 is default port, changable)
```
airflow webserver -p 8080
```

If another process is running on the port, use `top` to check all the running process. Then you can kill the previous running airflow/ the process with specific PID:
```
killall -9 airflow
kill -9 PID <PID>
```

Step 6: Create user
```
airflow users create --username admin --firstname Stanley --lastname Chan --role Admin --email stanleykinnok.chan@gmail.com
```

Step 7: Login to http://localhost:8080/ (8080 is changable)

Step 8: Start the airflow Scheduler in another terminal
```
airflow scheduler
```


**Extra:**
To stop loading example DAG, change the airflow.cfg parameter `load_examples = False`