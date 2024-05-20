# How to setup Airflow with Docker in 5 minutes
 if folders are not created

    mkdir ./dags ./plugins ./logs

dags stored in local dags will automatically sync to container dag folder

copy or move dags in source_dags folder to ./dags

# On Macos or Linux
### make sure user and group permissions are same between host and container
 
    echo -e "AIRFLOW_UID=$(id -u)\nAIRFLOW_GID=0" > .env
    docker-compose up airflow-init
    docker-compose up

#Airflow UI
    
    http://localhost:8080/ 
    username: airflow
    password: airflow

#Interact Airflow command line interface example

    docker exec [CONTAINER_ID] airflow version

#API

    curl -X GET --user "airflow:airflow" "http://localhost:8080/api/v1/dags"

#Docker commands

    docker-compose down && docker-compose up

![Alt text](images/screenshot.png?raw=true "Airflow UI DAG")
