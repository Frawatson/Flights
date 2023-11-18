# Flights

## Overview

This repository contains the source code for a javascript, HTML and CSS Applicatoin. The application is hosted on a Kubernetes cluster, and the deployment process is automated using Jenkins CI/CD pipeline.

## Technologies Used

- **HTML:** The structure of the web pages.
- **CSS:** Styling and layout of the application.
- **JavaScript:** Styling and layout of the application.
- **Docker:** containerize the application for deployment.
- **Kubernetes:** Container orchestration for deploying and managing the application.
- **Jenkins:** CI/CD pipeline automation tool.

## Prerequisites

Ensure you have the following tools installed before running the application locally:


- Docker
- Kubernetes CLI (kubectl)
- Jenkins

## Getting Started

1. Clone this repository to your local machine:

    ```bash
    git clone https://github.com/Frawatson/Flights.git
    ```

2. Navigate to the project directory:

    ```bash
    cd index.html
    ```

3. Run the application locally by opening the `index.html` file in your web browser.


4. ## modify the yaml files according to your needs

## Jenkins CI/CD Pipeline

The CI/CD pipeline automates the deployment process of this application to a Kubernetes cluster. Here are the main stages:

1. **Build:** Jenkins will trigger a build whenever changes are pushed to the `main` branch.

2. **Docker Image Build:** Build a Docker image containing the HTML/CSS application.

3. **Kubernetes Deployment:** Deploy the application to the Kubernetes cluster.

## Deployment to Kubernetes

The application is deployed to the Kubernetes cluster using the configuration files in the `kubernetes/` directory. The deployment includes services, deployments, and any necessary configurations.

