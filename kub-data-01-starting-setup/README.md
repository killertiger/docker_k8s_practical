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
kubectl apply -f=service.yaml -f=deployment.yaml -f=host-pvc.yaml -f=host-pv.yaml -f=environment.yaml
```

Checking volumes
```
$ kubectl get pv
NAME      CAPACITY   ACCESS MODES   RECLAIM POLICY   STATUS   CLAIM              STORAGECLASS   VOLUMEATTRIBUTESCLASS   REASON   AGE
host-pv   1Gi        RWO            Retain           Bound    default/host-pvc   standard       <unset>                          42s

$ kubectl get pvc
NAME       STATUS   VOLUME    CAPACITY   ACCESS MODES   STORAGECLASS   VOLUMEATTRIBUTESCLASS   AGE
host-pvc   Bound    host-pv   1Gi        RWO            standard       <unset>                 22s
```

## Running

Running service
```
minikube service story-service
```


GET  http://127.0.0.1:60601/story

POST
```json
{
    "text": "My text"
}
```

Raise error
GET http://127.0.0.1:60601/error


## Documentation

### hostPath
Mount the volume in the host path. It is a valid solution only for development.
In case of multiple hosts, this solution will not work.
```
volumes:
- name: story-volume
  hostPath:
    path: 
```

### Persistent Volume
Is detached from the pods
