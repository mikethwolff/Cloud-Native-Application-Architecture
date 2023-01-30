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

Argo CD:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-ui.png)

![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-prod.png)

# How do we get there:

1) **Task 1 - Create a Dockerfile, build & test the Docker image**

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

Create a GitHub Action to package and push the updated application image to DockerHub.

dockerhub.yml
```
name: Build and push to Docker Hub
on:
  release:
    types: [ created ]
  workflow_dispatch:
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v3
      - name: Log in to registryx
        uses: docker/login-action@v2
        with: 
          username: ${{ secrets.DOCKER_HUB_USERNAME }}
          password: ${{ secrets.DOCKER_HUB_PASS }}
      - name: Set up Docker Buildx
        id: buildx
        uses: docker/setup-buildx-action@v1
      - name: Build and push the image
        id: docker_build
        uses: docker/build-push-action@v2
        with:
          context: ./project
          file: ./project/Dockerfile
          push: true
          tags: ${{ secrets.DOCKER_HUB_USERNAME }}/<your-application>:latest
      - name: Image digest
        run: echo ${{ steps.docker_build.outputs.digest }}
```


3) **Task 3 - Kubernetes Declarative Manifests**

The application will be deployed along with a Kubernetes cluster using Minikube in this stage. Declarative Kubernetes manifests will be made, and the application will be released to the sandbox environment. You ought to have a set of YAML manifests that will control how the TechTrends application is handled by the cluster by the end of this stage.

The following Kubernetes manifests can be found:
```
project/kubernetes/deploy.yaml

project/kubernetes/namespace.yaml

project/kubernetes/service.yaml
```
Kubernetes:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/kubernetes-declarative-manifests.png)

4) **Task 4 - Helm Charts**

Throughout this stage, you will parameterize the application manifests using a template configuration manager like Helm. The program will be released to several settings using a Helm Chart template that we will create. We ought to have a set of parametrized YAML manifests that leverage an input values file to produce legitimate Kubernetes objects as a consequence.

The following manifests can be found:
```
project/helm/values.yaml

project/helm/values-staging.yaml

project/helm/values-prod.yaml
```

5) **Task 5 - Continuous Delivery with ArgoCD**

The deployment of the desired application states in the designated target settings is automated by Argo CD. Application deployments can keep track of changes made to branches, tags, or manifests pinned to a certain commit version.

Staging:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-staging.png)

Production:
![alt text](https://github.com/mikethwolff/Cloud-Native-Application-Architecture/blob/main/project/screenshots/argocd-techtrends-prod.png)





