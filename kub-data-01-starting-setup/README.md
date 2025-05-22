# Kub Action 01 Starting Setup

Based on course (Docker & Kubernetes: The Practical Guide [2025 Edition])[https://bairesdev.udemy.com/course/docker-kubernetes-the-practical-guide]

Section 13: Managing Data & Volumes with Kubernetes

## Dependencies

- minicube
- kubectl

## Setup

### Step by step
Setup
```bash
kubectl apply -f=deployment.yaml
kubectl apply -f=service.yaml
```

```bash
kubectl get deployments
kubectl get services
```

### Setup all
Using merged file

```bash
kubectl apply -f master-deployment.yaml
```

## Running

Running with minikube
```bash
minikube service backend
```

Root page:
```
/
```

Error page that crashes the app:
```
/error
```

## Clean up
Clean by imperative approach
```bash
kubectl delete deployments second-app-deployment
kubectl delete services backend
```

Clean by declarative approach
```bash
kubectl delete -f=deployment.yaml -f=service.yaml
```

