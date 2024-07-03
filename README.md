## Airflow
# Contents
- Introduction
- Installing Airflow

About Airflow:

Airflow is a popular tool that simplifies the complex workflow. It allows you to programmatically define, schedule, and monitor your workflows, all in one place. While Airflow is a powerful option, installation can sometimes feel overwhelming. This guide will break down the setup process into two easy-to-follow methods, getting you up and running with Airflow in no time.

This guide will focus on installing Airflow using Docker/podman. To follow along, make sure you have Docker Desktop up and running on your machine.

The docker-compose.yaml file includes the following service definitions: 
- airflow-scheduler: Manages and schedules tasks and DAGs.
- airflow-webserver: Hosts the web interface accessible at localhost:8080 .
- airflow-worker: Executes tasks assigned by the scheduler.
- airflow-init: Initializes the Airflow setup. 
- flower: Monitors and provides insights into the environment. It is available at localhost:5555 .
- postgres: Serves as the database.
- redis: Facilitates message forwarding from the scheduler to the workers.

Besides the common environment variables for the airflow services, they have four volumes: dags, logs, config and plugins. So we need to create 4 folders in local machine for Airflow Volumes
