# Tomcat 8.5.42 + Birt 4.8.0

This repo contains Dockerfile for Appache Tomcat 8.5.42 + BIRT Report Viewer 4.8.0 (Latest 05.07.2019)
- Image size: 645MB
- Installed birt drivers: **MSSQL Jdbc Connector, PostgreSQL Jdbc Connector** 
- Birt path: birt-viewer (http://yourmachine/birt-viewer)
- Deleted tomcat webapps: ROOT, examples, docs
## Configuration
- In **.env** file you can change mount paths for: tomcat/bin, tomcat/conf, birt-viewer/report
  ```
  #PATHS
  # Tomcat configuration folders
  TOMCAT_BIN=./birt/tomcat_configuration/bin
  TOMCAT_CONFIGS=./birt/tomcat_configuration/conf
  # Birt reports folder
  BIRT_REPORTS=./birt/reports 
  ```
- In **docker-compose.yml** you can change default port. Format: HOST_PORT:CONTAINER_PORT
  ```
  ports:
        - 80:8080
  ```
- In **birt/tomcat_configuration/bin/setenv.sh** you can change java virtual machine settings. For example:
  ```
  export CATALINA_OPTS="$CATALINA_OPTS -Xms512m"
  export CATALINA_OPTS="$CATALINA_OPTS -Xmx8192m"
  export CATALINA_OPTS="$CATALINA_OPTS -XX:MaxPermSize=256m"
  ```
  
## Build and Run

- Firts you should have installed Docker Engine and Docker Compose
- Clone repo:
  ``` 
  git clone https://github.com/RomanWebDev/tomcat-birt-docker.git
  ```
- Next compouse image:
  ```
  docker-compose build
  ```
- And run it:
  ```
  docker-compose up
  ```
