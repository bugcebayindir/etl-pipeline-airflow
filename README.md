# ETL Pipeline Airflow

### Introduction

In my other [repository](https://github.com/bugcebayindir/etl-pipeline-docker.git), we built ETL pipeline that carries out extract, transform and load tasks of transactional data via Docker. In this repository, pipeline is executed by using airflow docker image.

For pipeline, dag is created under airflow-dags folder which is importing definitions from src folder. Dag contains:
- DummyOperators are used as start dag and end dag
- PythonOperator carries out extract, transform and load tasks.

### Requirements
The minimum requirements:

- Docker for Mac: [Docker](https://docs.docker.com/desktop/install/mac-install/) 
- Docker for Windows:
  - Installation: [Docker](https://docs.docker.com/desktop/install/windows-install/)
  - Manual installation steps for older WSL version: [Docker WSL 2](https://learn.microsoft.com/en-us/windows/wsl/install-manual#step-4---download-the-linux-kernel-update-package)
- AWS Redshift connection details
- AWS S3 Bucket details

### Instructions on how to execute the code

Copy the .env.example file to .env and fill out the environment variables.

First, open Docker Desktop.

Make sure you are executing the code from the airflow folder.

- To run it locally first build the docker image with puckel/docker-airflow:

```bash
docker image build -t local-airflow .
```

- To run airflow with .env at localhost:8080:
```bash
docker run --env-file .env -d -p 8080:8080 local-airflow webserver
```

- To access airflow webserver at [http://localhost:8080/](http://localhost:8080/) and change status of the dag to 'On'.

