## CI/CD Pipeline

This repository includes a Jenkins CI/CD pipeline for automating the build, test, and deployment process of my application. The pipeline consists of several stages, each with its specific purpose.

### Pipeline Overview

The CI/CD pipeline orchestrates the following key stages:

- **Sonar Quality Check**: This stage performs static code analysis using SonarQube, ensuring the code meets quality standards. It also checks if the quality gate is passed.

- **Build Docker Images and Push to Nexus**: In this stage, the pipeline builds Docker images and pushes them to a Nexus Repository, making them available for deployment.

- **Push Helm Charts to Nexus Repo**: This stage packages Helm charts and uploads them to a Nexus Repository, facilitating Kubernetes deployments.

- **Deployment Approval**: The pipeline triggers an approval request, allowing manual approval or rejection of the deployment.

- **Deploy Application on Kubernetes Cluster**: If approved, the pipeline deploys the application on a Kubernetes cluster using Helm charts.

- **Verify Application Deployment on Kubernetes Cluster**: This stage tests the deployed application on the Kubernetes cluster to ensure it's functioning correctly.

### Pipeline Configuration

The pipeline is configured with several environment variables:

- `VERSION`: Represents the build version, typically derived from the Jenkins build ID.

- `DOCKER_HOSTED_EP`: Refers to the Docker registry endpoint where Docker images are hosted.

- `HELM_HOSTED_EP`: Points to the Helm repository endpoint for storing Helm charts.

### Deployment Approval

The "Deployment Approval" stage is designed for human intervention. It sends notification emails and messages to request deployment approval, enabling users to approve or reject the deployment.

### Post-build Actions

After the pipeline completes, post-build actions send notifications about the build's status to relevant parties via email and Slack.

### Usage

To use this CI/CD pipeline, make sure to configure the necessary environment variables, credentials (e.g., SonarQube token and Nexus credentials), and ensure that Jenkins is set up to trigger the pipeline.

Remember to customize the pipeline according to your project's specific requirements.

Please note that the pipeline depends on Jenkins, SonarQube, Docker, Nexus Repository, Helm, and a Kubernetes cluster, so ensure that these components are correctly configured.

For any questions or assistance, feel free to contact "zerqqaouiyassine1@gmail.com".
