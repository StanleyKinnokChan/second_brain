
### **Step1: create yml file**

**docker-compose.yml**
```
version: "3.8"

services:

  db:

    container_name: postgres_container

    image: postgres:13-alpine

    restart: always

    environment:

      POSTGRES_USER: root

      POSTGRES_PASSWORD: root

      POSTGRES_DB: test_db

    ports:

      - "5432:5432"

  pgadmin:

    container_name: pgadmin4_container

    image: dpage/pgadmin4

    restart: always

    environment:

      PGADMIN_DEFAULT_EMAIL: admin@admin.com

      PGADMIN_DEFAULT_PASSWORD: root

    ports:

      - "5050:80"
```


### Step2: Go to http://localhost:5050/ and login with the info in the docker-compose.yml

### Step3: Build connection
use `docker container ls` to see the container id and use `docker inspect` to get the IP of the container