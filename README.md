# Airflow
## Contents
- Introduction
- Installing Airflow

### About Airflow:

Airflow is a popular tool that simplifies the complex workflow. It allows you to programmatically define, schedule, and monitor your workflows, all in one place. While Airflow is a powerful option, installation can sometimes feel overwhelming. This guide will break down the setup process into two easy-to-follow methods, getting you up and running with Airflow in no time.

This guide will focus on installing Airflow using Docker/podman. To follow along, make sure you have Docker Desktop up and running on your machine.

### Installing Airflow:

#### Components
The docker-compose.yaml file includes the following service definitions: 

- airflow-scheduler: Manages and schedules tasks and DAGs.
- airflow-webserver: Hosts the web interface accessible at localhost:8080 .
- airflow-worker: Executes tasks assigned by the scheduler.
- airflow-init: Initializes the Airflow setup. 
- flower: Monitors and provides insights into the environment. It is available at localhost:5555 .
- postgres: Serves as the database.
- redis: Facilitates message forwarding from the scheduler to the workers.

#### Volumes:

Besides the common environment variables for the airflow services, we have four volumes: dags, logs, config and plugins. So we need to create 4 folders in local machine for Airflow Volumes

- dags: For placing the DAG scripts
- logs: For placing logs of airflow
- config: For Airflow Configurations
- plugins: For any Extra Plugins 

Please check the docker Compose file in the Repo. 

#### Permissions:
For seamless volume synchronization, we need to confirm that the UID (user ID) and GID (group ID) permissions on the Docker volumes align with those on the local filesystem.

In YAML file:

```user: "${AIRFLOW_UID:-50000}:0"```

In Local Environment

```echo -e "AIRFLOW_UID=$(id -u)" > .env```

```echo -e "AIRFLOW_GID=0" > .env```

Post this steps your .env file looks as below 

AIRFLOW_UID=501
AIRFLOW_GID=0

#### Run Docker Compose:
Once we have all the setup we can run the docker compose file using below command

 ```docker-compose up airflow-init```

#### Login into Airflow:
Once you see all the containers up and running you can open localhost:8080 in browser and login to airflow with admin creds

Username : admin
Password :  airflow

 We've successfully installed the full version of Airflow in just a few minutes using Docker.

