# How to setup Airflow with Docker in 5 minutes
 if folders are not created

    mkdir ./dags ./plugins ./logs ./db ./processed_data

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
    
    docker ps | grep web
    docker exec -it [CONTAINER_ID] bash #start bash session inside container
    docker exec [CONTAINER_ID] airflow version

#API

    curl -X GET --user "airflow:airflow" "http://localhost:8080/api/v1/dags"

#Docker commands to stop and start

    docker-compose down && docker-compose up

# Two Custom Dags
    my_dag.py
        model accuracy pipeline
    dags/data_ingestion_dag
        etl pipeline

# Install DBEaver Community Edition Command Line

    brew install --cask dbeaver-community

# Install from Web
    
    https://dbeaver.io/download/

![Alt text](images/screenshot.png?raw=true "Airflow UI DAG")
![Alt text](images/booking.png?raw=true "ETL Client Hotel Booking")
![Alt text](images/dbeaver.png?raw=true "DBEaver")

# Clean up and Prune

    docker container prune

or

which will clean up all unused containers, networks, images (both dangling and unreferenced), and optionally, volumes, in one command.

    docker system prune

Remove unused local volumes

    docker volume prune

Remove all images

    docker image prune -a