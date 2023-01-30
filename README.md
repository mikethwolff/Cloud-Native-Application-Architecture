# Cloud-Native Application Architecture

*The listed projects were part of, or based on the Cloud Native Application Architecture Udacity nanodegree program and are displayed in derivated or amended form due to possible copyright restrictions.*

*Form and requirements of my projects may differ from present projects. Udacity may vary projects and this repo is representing my findings at this point in time and may not be representative for future Cloud Native Application Architecture projects. If you are currently enrolled into Udacity's Cloud Native Application Architecture Nanodegree please keep in mind that my findings may help you as a guide but copying these findings will go against Udacity's Honor Code.*

# Project 1: Automated CI/CD pipeline using Argo CD, GitHub Actions, Helm, Kubernetes, Docker & Python

This project covers the following steps:

- Docker for Application Packaging
- Continuous Integration with GitHub Actions
- Kubernetes Declarative Manifest
- Helm Charts
- Continuous Delivery with ArgoCD

# Wished outcome: Synchronized applications in ArgoCD

![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-prod.png)

How do we get there:

1) **Task 1 - Create a Dockerfile, Build & test the Docker image**

This can be achieve by using the following commands:

docker build -t <your-app-name> .
Notice the dot at the end of the command stands for the same directory

Docker command used to run the application and expose port:
docker run -d -p  7111:3111 <your-app-name>
  
Docker commands used to get the application logs
docker logs <your-container-id>



