# Kub Action 01 Starting Setup

Based on course (Docker & Kubernetes: The Practical Guide [2025 Edition])[https://bairesdev.udemy.com/course/docker-kubernetes-the-practical-guide]


## Dependencies

minicube
kubectl

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

Running on minikube
```bash
minikube service backend
```


## Clean up
Clean by item
```bash
kubectl delete deployments second-app-deployment
kubectl delete services backend
```

Clean by declarative way
```bash
kubectl delete -f=deployment.yaml -f=service.yaml
```
