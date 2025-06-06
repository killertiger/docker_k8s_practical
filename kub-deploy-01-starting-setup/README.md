# Kub Networking 01 Starting Setup

Based on course (Docker & Kubernetes: The Practical Guide [2025 Edition])[https://bairesdev.udemy.com/course/docker-kubernetes-the-practical-guide]

Section 15: Kubernetes Deployment (AWS EKS)

## Dependencies

- kubectl

## Setup

Create a repository in dockerhub

Build images

```bash
docker build -t killertiger/kub-dep-users .
docker build -t killertiger/kub-dep-auth .
```

Push image

```bash
docker push killertiger/kub-dep-users
docker push killertiger/kub-dep-auth
```


Apply configuration
```
kubectl apply -f=users-deployment.yaml -f=users-service.yaml
kubectl apply -f=auth-deployment.yaml -f=auth-service.yaml
```


Create a key in https://us-east-1.console.aws.amazon.com/iam/home?region=us-east-1#/security_credentials and use the following command to set up
```
aws configure
```

Setup kubectl
```
aws eks --region us-east-1 update-kubeconfig --name kub-dep-demo
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


