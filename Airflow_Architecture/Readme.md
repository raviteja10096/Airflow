# Apache Airflow Architecture Simplified

## Contents
- Introduction
- Architecture
- Components
  - 𝗪𝗲𝗯 𝗦𝗲𝗿𝘃𝗲𝗿🌐
  - 𝗦𝗰𝗵𝗲𝗱𝘂𝗹𝗲𝗿 🕰️
  - 𝗘𝘅𝗲𝗰𝘂𝘁𝗼𝗿 ⚙️
  - 𝗪𝗼𝗿𝗸𝗲𝗿 👷
  - 𝗠𝗲𝘁𝗮𝗱𝗮𝘁𝗮 𝗗𝗮𝘁𝗮𝗯𝗮𝘀𝗲 🛢
  - 𝗠𝗲𝘀𝘀𝗮𝗴𝗲 𝗕𝗿𝗼𝗸𝗲𝗿 ✉︎ ✉︎ ✉︎(𝗼𝗽𝘁𝗶𝗼𝗻𝗮𝗹)

## Apache Airflow Architecture:

### Introduction
Apache Airflow is an open-source platform designed for orchestrating complex data workflows. It uses Directed Acyclic Graphs (DAGs) to define a series of tasks and their dependencies. Airflow is made up of several microservices that collaborate to execute these tasks. Here’s a straightforward breakdown of the key components of airflow Architecture.

### Architecture:

![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Airflow%20Arch%20New%20Updated.gif)


### Components:

𝗪𝗲𝗯 𝗦𝗲𝗿𝘃𝗲𝗿 🌐: Airflow UI where you can monitor, and manage DAGs, Variables, connections and check the logs. It provides a dashboard that helps you visualize your data workflows, check their progress, and troubleshoot any issues.
![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Component%20GIFS/Airflow_Webserver.gif)

𝗦𝗰𝗵𝗲𝗱𝘂𝗹𝗲𝗿 🕰️: It is responsible for managing the execution of tasks. It monitors the DAGs and schedules tasks to run based on their dependencies and timing configurations. It makes sure that tasks are executed in the right order and at the right time.
![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Component%20GIFS/Airflow_Scheduler.gif)

𝗘𝘅𝗲𝗰𝘂𝘁𝗼𝗿 ⚙️: The Executor’s primary role involves executing tasks actively. It interacts with the Scheduler to obtain task details and initiates the required processes or containers for task execution.

Airflow offers various Executor types like LocalExecutor, CeleryExecutor, and KubernetesExecutor, each tailored to specific infrastructure setups and operational needs.
![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Component%20GIFS/Airflow_executor.gif)

𝗪𝗼𝗿𝗸𝗲𝗿 👷:The Worker is a component that performs the tasks assigned by the Executor. Depending on the chosen Executor, it can be a separate process or container. Workers are responsible for executing the actual code or scripts defined in your tasks and reporting their status back to the Executor.
![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Component%20GIFS/Airflow_Worker.gif)

𝗠𝗲𝘁𝗮𝗱𝗮𝘁𝗮 𝗗𝗮𝘁𝗮𝗯𝗮𝘀𝗲 🛢: This is where Airflow keeps track of all your workflows, including details about the tasks you’ve set up and how they’ve run in the past. It’s like a central hub for storing and organizing everything related to your scheduled tasks. This helps you keep an eye on how things are progressing and troubleshoot any issues that might come up. Airflow gives you the flexibility to use different databases like PostgreSQL, MySQL, or SQLite to store this information, depending on what works best for your setup.
![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Component%20GIFS/Airflow_MetadataBase.gif)

𝗠𝗲𝘀𝘀𝗮𝗴𝗲 𝗕𝗿𝗼𝗸𝗲𝗿 ✉︎ ✉︎ ✉︎(𝗼𝗽𝘁𝗶𝗼𝗻𝗮𝗹): In setups where the CeleryExecutor is used for distributing tasks, a message broker plays a crucial role. This broker, like RabbitMQ or Redis, acts as a middleman between the Scheduler and the Workers. It ensures smooth communication by passing task details from the Scheduler to the Workers, ensuring tasks are executed reliably and efficiently across the distributed system.
![image](https://github.com/raviteja10096/Airflow/blob/main/Airflow_Architecture/Component%20GIFS/Airflow_message_Broker.gif)

