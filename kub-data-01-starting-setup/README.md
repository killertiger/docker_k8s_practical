# Kub Action 01 Starting Setup

Based on course (Docker & Kubernetes: The Practical Guide [2025 Edition])[https://bairesdev.udemy.com/course/docker-kubernetes-the-practical-guide]

Section 13: Managing Data & Volumes with Kubernetes

## Dependencies

- minicube
- kubectl

## Setup

Create a repository in dockerhub

Build image

```bash
docker build -t killertiger/kub-data-demo .
```

Push image

```bash
docker push killertiger/kub-data-demo
```

Ensure that minikube is running
```bash
minikube status
```

If minikube is not running
```
minikube start --driver=docker
```

Apply configuration
```
kubectl apply -f=service.yaml -f=deployment.yaml
```

## Running

Running service
```
minikube service story-service
```