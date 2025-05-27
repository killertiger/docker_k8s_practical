# Kub Networking 01 Starting Setup

Based on course (Docker & Kubernetes: The Practical Guide [2025 Edition])[https://bairesdev.udemy.com/course/docker-kubernetes-the-practical-guide]

Section 14: Kubernetes Networking

## Dependencies

- minicube
- kubectl

## Setup

Create a repository in dockerhub

Build images

```bash
docker build -t killertiger/kub-demo-users .
docker build -t killertiger/kub-demo-tasks .
docker build -t killertiger/kub-demo-auth .
docker build -t killertiger/kub-demo-frontend .
```

Push image

```bash
docker push killertiger/kub-demo-users
docker push killertiger/kub-demo-tasks
docker push killertiger/kub-demo-auth
docker push killertiger/kub-demo-frontend
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
kubectl apply -f=users-deployment.yaml -f=users-service.yaml
kubectl apply -f=tasks-deployment.yaml -f=tasks-service.yaml
kubectl apply -f=auth-deployment.yaml -f=auth-service.yaml
kubectl apply -f=frontend-deployment.yaml -f=frontend-service.yaml
```



## Running

Running service
```
minikube service users-service
```


GET  http://127.0.0.1:60601/story

POST
```json
{
    "email": "test@test.com",
    "password": "test"
}
```

Raise error
GET http://127.0.0.1:60601/error


