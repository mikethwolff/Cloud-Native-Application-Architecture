# Cloud-Native Application Architecture

*The listed projects were part of - or based on - the Cloud-Native Application Architecture Udacity program and are displayed in derivated or amended form due to possible copyright restrictions.*

*Form and requirements of my projects may differ from present projects. Udacity may vary projects and this repo is representing my findings at this point in time and may not be representative for future Cloud-Native Application Architecture projects. If you are currently enrolled into Udacity's Cloud-Native Application Architecture program please keep in mind that my findings may help you as a guide but copying these findings will go against Udacity's Honor Code.*

# Project 1: Automated CI/CD pipeline using Argo CD, GitHub Actions, Helm, Kubernetes, Docker & Python

This project covers the following steps:

- Docker for Application Packaging
- Continuous Integration with GitHub Actions
- Kubernetes Declarative Manifest
- Helm Charts
- Continuous Delivery with ArgoCD

# Wished outcome: Synchronized applications in ArgoCD

![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-prod.png)

# How do we get there:

1) **Task 1 - Create a Dockerfile, Build & test the Docker image**

This step focuses on packaging the application using Docker. We will need to write a Dockerfile and build a Docker image. By the end of this step, we should have the application running locally inside a Docker container.

This can be achieve by using the following commands:
```
docker build -t <your-app-name> .
```
Notice the dot at the end of the command stands for the same directory

Docker command used to run the application and expose port:
```
docker run -d -p  7111:3111 <your-app-name>
```
Docker commands used to get the application logs:
```
docker logs <your-container-id>
```

2) **Task 2 - Continuous Integration with GitHub Actions**

Here we use the CI (Continuous Integration) to automate application packaging. The application Docker image is created, tagged, and uploaded to DockerHub using GitHub Actions. Finally, a working GitHub Action that creates a fresh image for each new commit to the main branch will be available.

3) **Task 3 - Kubernetes Declarative Manifests**

Kubernetes:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/kubernetes-declarative-manifests.png)

4) **Task 4 - Helm Charts**

Throughout this stage, you will parameterize the application manifests using a template configuration manager like Helm. The program will be released to several settings using a Helm Chart template that we will create. We ought to have a set of parametrized YAML manifests that leverage an input values file to produce legitimate Kubernetes objects as a consequence.

5) **Task 5 - Continuous Delivery with ArgoCD**

The deployment of the desired application states in the designated target settings is automated by Argo CD. Application deployments can keep track of changes made to branches, tags, or manifests pinned to a certain commit version.

Argo CD:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-ui.png)

Staging:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-staging.png)

Production:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-prod.png)





