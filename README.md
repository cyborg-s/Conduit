# Conduit

## Contanization of a frontend and backend application

This repository is a guide for the containerization of a simple [Frontend](https://github.com/cyborg-s/conduit-frontend) and corresponding [Backend](https://github.com/cyborg-s/conduit-backend) application.

This repository was created as part of my continuing education at the **Developer Academy**.

## Table of Contents

* [Conduit](#conduit)
    1. [Containzation of a frontend and backend application](#contanization-of-a-frontend-and-backend-application) 
    2. [Table of Contents](#table-of-contents)
    3. [Prerequisites](#prerequisites)
    4. [Description](#description)
       1. [What is Conduit](#what-is-conduit)
       2. [Conduit with Docker](#conduit-with-docker)
       3. [Folder structure of the Contaization](#folder-structure-of-the-containerization)
    5. [Quickstart](#quickstart)
    6. [Usage](#usage)



## Prerequisites

  * **Docker**
  * **Compose**

## Description

### What is Conduit

Conduit, also known as the RealWorld Example App, is an open-source example application that serves as a Medium.com-like blogging platform. 

It demonstrates best practices in modern web stacks, both for the frontend (e.g. Angular, React, Vue) and the backend (e.g. Django, Node.js, Rails). 

The app is often used as a reference project to learn and test complete full-stack applications with authentication, CRUD functionality and API interactions.

It is provided free by [Thinkster](https://thinkster.io/)


### Conduit with Docker

Starting the frontend and backend in a container simplifies the environment configuration and makes the application portable, as all dependencies are bundled. 
    
It also facilitates local testing and debugging without separate servers or network configuration.


### Folder structure of the Containerization
```
Conduit_Deploy/
    ├── .github/workflows
      ├── deployment.yml
      └── README.md
    ├── backend
        ├── Dockerfile
        └── entrypoint.sh
    ├── frontend
        └── Dockerfile
    ├── compose.yml
    ├── example.env
    └── README.md
```

## Quickstart

This section gives brief and minimal instructions on how to use the setup. More in-depth instructions can be found in the [Usage](#usage) section.

1. Clone the project to your platform:

   ```bash
   git clone git@github.com:cyborg-s/Conduit_Deploy.git
   ```

2. Navigate to the project directory:

   ```bash
   cd Conduit_Deploy
   ```

3. Create the `.env` file from the template and edit your own settings:
   
   ```bash 
   cp example.env .env
   ``` 

4. Build and start the container in the background:

   ```bash
   docker compose up --build -d
   ```


5. Check whether the server is running correctly:

    * Conduit can be accessed at the IP address of your VM on port 8282:

      ```bash  
      http://<Your_VM_IP>:8282
      ```  

    * The backend adminpanel can be accessed at the IP adress of your VM on port 2828:
  
      ```bash  
      http://<Your_VM_IP>:2828/admin
      ```  
    
  

## Usage


### Manage the container:
  
  * Show the log files:
    ```bash
    docker compose logs <CONTAINER_NAME> -f
    ```

  * Save the logs:
    ```bash
    docker compose logs <CONTAINER_NAME> -f > <NAME>.txt
    ```

  * Stop the container:
    ```bash
    docker compose stop <CONTAINER_NAME>
    ```

  * Delete the container:
    ```bash
    docker compose down <CONTAINER_NAME>
    ```

  * List all containers that are operatet by Docker Compose:
    ```bash
    docker compose ps
    ```

###  If no network is defined in the compose file, docker automatically creates one. 
   *  To check which networks exist:

        ```bash
        docker network ls
        ```

   * To list which containers are on a network:

        ```bash
        docker network inspect <NETWORK_NAME>
        ```

   * To check if the wordpress and mariadb container are in the same network:

        ```bash
        docker network inspect conduit_deploy_conduit-network 
        ```  

    