# Java Maven CI/CD Deployment on AWS

## Project Overview

This project demonstrates an end-to-end DevOps workflow for building, containerizing, and deploying a Java Maven web application on AWS.

The base Java Maven application was forked from the original `Premvikash/java-maven-sample-war` repository and used as the application layer for implementing my DevOps CI/CD and cloud deployment workflow.

## DevOps Workflow

The application follows this deployment flow:

**Developer → GitHub → Jenkins → Maven → Docker → Kubernetes (Amazon EKS) → AWS Load Balancer → User**

## Technologies Used

* Git & GitHub
* Jenkins
* Apache Maven
* Docker
* Kubernetes
* Amazon EKS
* Amazon EC2
* AWS Elastic Load Balancing
* AWS EFS

## Project Implementation

### 1. Source Code Management

The application source code is maintained in GitHub and used as the source repository for the CI/CD workflow.

### 2. Maven Build

Apache Maven is used to compile and package the Java web application.

```bash
mvn clean package
```

The Maven build generates a WAR artifact inside the `target/` directory.

### 3. Jenkins CI/CD

Jenkins is used to automate the application build and deployment workflow.

The pipeline performs tasks such as:

* Pulling the latest source code from GitHub
* Running the Maven build
* Generating the WAR artifact
* Preparing the application for containerization and deployment

### 4. Docker Containerization

The generated WAR application is packaged into a Docker image using Apache Tomcat as the application server.

Example:

```bash
docker build -t registerapp:latest .
```

The containerized application can then be deployed consistently across environments.

### 5. Kubernetes Deployment

Kubernetes is used to orchestrate the application containers.

The application was deployed using Kubernetes resources such as:

* Deployment
* ReplicaSet
* Pods
* Service

Multiple replicas were used to demonstrate application availability and container orchestration.

### 6. Amazon EKS

Amazon Elastic Kubernetes Service (EKS) was used as the managed Kubernetes environment on AWS.

The Dockerized Java application was deployed to the EKS cluster and managed using `kubectl`.

Example:

```bash
kubectl get nodes
kubectl get deployments
kubectl get pods
kubectl get services
```

### 7. AWS Load Balancer

A Kubernetes `LoadBalancer` service was used to expose the application externally.

The AWS load balancer provided a public endpoint through which the deployed application could be accessed.

### 8. Persistent Storage

AWS EFS was integrated with Kubernetes using PersistentVolume and PersistentVolumeClaim resources to demonstrate persistent storage for workloads running inside the cluster.

## Architecture

```text
                    GitHub
                       |
                       v
                    Jenkins
                       |
                       v
                     Maven
                       |
                       v
                  WAR Artifact
                       |
                       v
                    Docker
                       |
                       v
                 Docker Image
                       |
                       v
                 Amazon EKS
                       |
              Kubernetes Deployment
                       |
                 ReplicaSet
                       |
                    Pods
                       |
                       v
              AWS Load Balancer
                       |
                       v
                     User
```

## Key Skills Demonstrated

* CI/CD pipeline implementation
* Maven build automation
* Docker containerization
* Kubernetes deployments and services
* Amazon EKS cluster deployment
* AWS load balancing
* Persistent storage using AWS EFS
* Git/GitHub version control
* Troubleshooting Kubernetes workloads

## Repository Note

This repository was originally forked from `Premvikash/java-maven-sample-war`.

The base Java Maven application was used for learning and implementing the DevOps workflow. The CI/CD, Docker, Kubernetes, AWS EKS, EFS, load-balancing, deployment, and infrastructure-related work documented here represents the DevOps implementation performed as part of this project.
