# Survey Python Application

## Overview
This project is a survey application built using Python. The application is containerized using Docker, allowing for easy deployment and scaling. The Docker image is pushed to Docker Hub and managed using Kubernetes for orchestration.

## Prerequisites
- Docker installed on your machine
- Kubernetes cluster (Minikube recommended)
- Ansible installed on your machine

## Installation Instructions
1. **Clone the repository**:
   git clone https://github.com/reemabobakr/python-app

2. **Run the Ansible playbook to automate the Docker image build and push process**:  
    Ensure you have the Ansible file ready and run:
        ansible-playbook playbook.yml
3. **Create a namespace in Kubernetes**:
     kubectl create namespace python-app
4. **Deploy the application on Kubernetes**:
      kubectl -n python-app apply -f deployment.yaml
5. **Create the service for the application** 
      kubectl -n python-app apply -f services.yaml     
6. **Access the application**:
     Get the URL to access the service:
        minikube service -n python-app survey-app --url

## Features
- Containerized using Docker for easy deployment and scaling.
- Managed through Kubernetes for orchestration.
- Automated build and deployment process using Ansible.

## Ansible Automation
 The Ansible playbook automates the following tasks:

- Stop and remove any existing Docker containers.
- Remove the existing Docker image.
- Build a new Docker image from the Dockerfile.
- Push the newly built Docker image to Docker Hub.
- Run the new container and perform necessary migrations.

        
