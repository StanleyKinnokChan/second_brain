Follows [this](https://airflow.apache.org/docs/apache-airflow/stable/howto/docker-compose/index.html)

**Step1:** Fetching docker-compose.yaml
```
curl -LfO 'https://airflow.apache.org/docs/apache-airflow/2.8.3/docker-compose.yaml'
```

If you don't need the distributed Task queue, which is done by CeleryExecutor, you might want to change the `AIRFLOW__CORE__EXECUTOR` parameter into LocalExecutor and delete the `AIRFLOW__CELERY__RESULT_BACKEND`, `AIRFLOW__CELERY__BROKER_URL` and `redis`, `celery worker` and `flower`

You can also stop airflow from loading the sample DAG by changing the parameter  `AIRFLOW__CORE__LOAD_EXAMPLES` into `false`

**Step2:** create directory for saving logs, DAG and all other files
```
mkdir -p ./dags ./logs ./plugins ./config
echo -e "AIRFLOW_UID=$(id -u)" > .env
```

**Step3:** Initialize the env and Run all services
```
docker compose up airflow-init
docker-compose up -d

```

