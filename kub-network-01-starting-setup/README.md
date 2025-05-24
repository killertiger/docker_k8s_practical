# Kub Networking 01 Starting Setup

Based on course (Docker & Kubernetes: The Practical Guide [2025 Edition])[https://bairesdev.udemy.com/course/docker-kubernetes-the-practical-guide]

Section 14: Kubernetes Networking

## Dependencies

- minicube
- kubectl

## Setup

Create a repository in dockerhub

Build image

```bash
docker build -t killertiger/kub-demo-users .
```

Push image

```bash
docker push killertiger/kub-demo-users
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
kubectl apply -f=users-deployment.yaml
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


