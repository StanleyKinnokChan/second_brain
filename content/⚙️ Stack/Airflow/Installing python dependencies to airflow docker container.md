---
title: 
tags:
---
There are two ways to do that: **Image Extending** & **Image Customising**

![[image extending vs cutomising.png]]
![[image extending vs cutomising2.png]]


1. **Image Extending**
	1.  Create requirements.txt with dependencies. Example: `scikit-learn==0.24.2`
	2. Define the extended image by creating Dockerfile
	   `FROM apache/airflow:2.0.1`
	   `COPY requirements.txt /requirements.txt`
	   `RUN pip install --user --upgrade pip`
	   `RUN pip install --no-cache-dir --user -r /requirements.txt`
	3. Build the image
	   `docker build . --tag extending_airflow:lates`
	4. Replace the image name in the docker compose
		   from: `image: ${AIRFLOW_IMAGE_NAME:-apache/airflow:2.8.3}` 
		   to: `image: ${AIRFLOW_IMAGE_NAME:-extending_airflow:latest}`
	5. Rebuild the  docker compose for webserver & scheduler`
		`docker compose up -d --no-deps --build airflow-webserver airflow-scheduler`

2. **Image Customizing**
	1. clone the airflow source code, open the folder
	2. Create requiremnets.txt in the docker-context-files
	3. Build the image
	   `docker build . --build-ar![[image extending vs cutomising2.png]]g ARIFLOW_VERSION='2.0.1 --tag cutomising_airflow:latest'
	4. Replace the image name in the docker compose
	5. Rebuild the docker compose for webserver & scheduler