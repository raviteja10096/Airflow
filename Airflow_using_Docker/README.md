# Airflow
![image](https://github.com/raviteja10096/Airflow/assets/33113373/616ab9f8-5782-4179-b13d-e9a1a131186a)

## Contents
- Introduction
- Installing Airflow
- Running Docker Compose
- Interacting with Airflow UI

### About Airflow:

Airflow is a popular tool that simplifies the complex workflow. It allows you to programmatically define, schedule, and monitor your workflows, all in one place. While Airflow is a powerful option, installation can sometimes feel overwhelming. This guide will break down the setup process into two easy-to-follow methods, getting you up and running with Airflow in no time.

**Sample Airflow UI:**
![image](https://github.com/raviteja10096/Airflow/assets/33113373/54f4ffde-96ce-4d5b-9bac-3f4bc969f7a7)


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

 ![image](https://github.com/raviteja10096/Airflow/assets/33113373/0f8ab18b-446e-400a-a4b5-b77eada33e22)

 
  ```docker compose up -d```
  
  ![image](https://github.com/raviteja10096/Airflow/assets/33113373/4da11f4d-42ec-4fb7-bdb5-630cf119bbaa)


#### Login into Airflow:
Once you see all the containers up and running you can open localhost:8080 in browser and login to airflow with admin creds

Username : airflow
Password :  airflow

Login Page

![image](https://github.com/raviteja10096/Airflow/assets/33113373/82c43f3f-6c82-46d2-98d4-79da627a9ede)

Home Page

![image](https://github.com/raviteja10096/Airflow/assets/33113373/01fc22e0-14f2-45f2-9c3d-2bd56f5fbfa6)


 We've successfully installed the full version of Airflow in just a few minutes using Docker.
 
 ![image](https://github.com/raviteja10096/Airflow/assets/33113373/a88309a7-c6be-49f1-8156-d7aa7277e6b0)

** References:**

Airflow Documentation - https://airflow.apache.org/docs/
