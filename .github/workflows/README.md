# Conduit CI/CD

## Deploy Conduit with GitHub Action 

This action workflow automatically clones or updates the Conduit project on the VM.
It can be triggered manually or automatically by a push, ensuring that the latest executable version of the project is always available.

## Table of Contents

* [Conduit](#conduit-cicd)
  * [Deploy with Actions](#deploy-conduit-with-github-action)
  * [Table of Contents](#table-of-contents)
  * [Description](#description)
  * [Required secrets](#required-secrets-and-variables)

## Description

  The workflow is triggered when you push to the branch, which defined in [Deployment.yml](./deployment.yml)

The CD pipline has two jobs:
    
   1. Build task: This task creates a Docker container image within GitHub Actions to outsource this task. 
   2. Deploy task: This job transfers the deployment files to the target server and starts the Conduit application using Docker Compose.


## Required secrets and variables

To execute the workflow and create the `.env` file for the cloning process, various GitHub Actions secrets and variables are required, which must be set for the repository.

<ins>You can define these under the following path:</ins>

  - >  Conduit repository > Settings > Security – Secrets and variables > Actions > Repository secrets

| Name | Secret | Description |
| ---  | ------ | ----------- |
| SSH_HOST | <YOUR_VM_IP_ADDRESS> | IP address of remote server |
| SSH_USER | <YOUR_VM_USERNAME> | Username on remote server |
| SSH_PRIVATE_KEY | <PRIVAT_SSH_KEY> | Private SSH key of remote server |
| DEPLOY_DIR | <PATH_TO_DEPLOY_DIR> | Path to the folder in which the project should be published |
| SECRET_KEY | <SECRET_KEY> | Essential cryptographic key used by Django to protect sensitive data and provide security-critical functionality |
| DEBUG | True/False | Set False for production mode |
| ALLOWED_HOSTS | <IP_ADRESS> | Comma-separated list of hostnames or IP addresses that are allowed to connect to the Django server |
| CORS_ORIGIN_WHITELIST | <IP_ADDRESS:FRONTEND_PORT> | List of all Origins with their portnumbers, added to [settings.py](../../backend/conduit/settings.py) |
| API_URL | <IP_ADRESS:PORT/api> | Adds backend URL to `environment.prod.ts`, used in `app/core/interceptors/api.interceptor.ts` |
| BACKEND_EXTERNAL_PORT | <BACKEND_PORT> | External portnumber for backend-container |
| FRONTEND_EXTERNAL_PORT | <FRONTEND_PORT> | External portnumber for frontend-container |
| DJANGO_SUPERUSER_EMAIL | <YOUR_EMAIL> | Email address to create a superuser for the admin panel |
| DJANGO_SUPERUSER_USERNAME | <YOUR_USERNAME> | Username to create a superuser for the admin panel |
| DJANGO_SUPERUSER_PASSWORD | <YOUR_PASSWORD> | Password to create a superuser for the admin panel |