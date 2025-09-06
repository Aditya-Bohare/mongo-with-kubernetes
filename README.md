# MongoDB + Mongo Express Kubernetes Deployment

This repository contains Kubernetes manifests to deploy a **MongoDB** database along with **Mongo Express**, a web-based MongoDB admin UI. The setup includes secure credential management using Kubernetes Secrets and ConfigMaps, and basic authentication for Mongo Express.

---

## Table of Contents

- [Prerequisites](#prerequisites)  
- [Setup and Deployment](#setup-and-deployment)  
- [Accessing Mongo Express](#accessing-mongo-express)  
- [Cleanup](#cleanup)  
- [Notes and Best Practices](#notes-and-best-practices)  

---

## Prerequisites

- A Kubernetes cluster (local like Minikube/Docker Desktop or cloud provider)  
- `kubectl` CLI installed and configured  
- Basic understanding of Kubernetes concepts (Secrets, ConfigMaps, Deployments, Services)  

---

## Setup and Deployment

### 1. Clone this repository

```bash
git clone https://github.com/Aditya-Bohare/mongo-with-kubernetes.git
cd mongo-with-kubernetes
```
### 2. Deploy the configMap and secret yml

```bash
kubectl apply -f ./mongo-secret.yml
kubectl apply -f ./mongoexpress-config.yml
```

### 3. Deploy the pod and service yml
```bash
kubectl apply -f ./mongodb-depl.yml
kubectl apply -f ./mongoexpress-depl.yml
```

### 4. Accessing mongo express ui in localhost:8081
```bash
kubectl port-forward service/mongo-express-service 8081:8081
```

### 5. Cleanup the deployment, service, configMap, secret
```bash
kubectl delete -f ./mongoexpress-depl.yaml
kubectl delete -f ./mongodb-depl.yaml
kubectl delete -f ./mongoexpress-config.yaml
kubectl delete -f ./mongo-secret.yaml
```


Found an issue or have a suggestion? Feel free to open an issue or submit a pull request!
