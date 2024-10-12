# Kubernetes E-Commerce Application Deployment

This project demonstrates the deployment of a simulated e-commerce application in a Kubernetes environment. The application is designed to ensure high availability, security, and scalability, and it includes multiple components such as a React frontend, Node.js backend services, MongoDB, and RabbitMQ.

## Table of Contents

- [Overview](#overview)
- [Architecture](#architecture)
- [Requirements](#requirements)
- [Project Structure](#project-structure)
- [Deployment Steps](#deployment-steps)
- [Networking and Ingress](#networking-and-ingress)
- [Monitoring and Autoscaling](#monitoring-and-autoscaling)
- [Debugging & Troubleshooting](#debugging--troubleshooting)
- [Contributing](#contributing)
- [License](#license)

## Overview

The e-commerce application consists of multiple components deployed within a Kubernetes cluster:
- **Frontend**: A React-based web application served by Nginx.
- **Backend API**: Node.js microservices that handle various business operations.
- **Database**: MongoDB cluster used for persistent data storage.
- **Message Queue**: RabbitMQ for asynchronous order processing.

This deployment focuses on providing scalable, secure, and observable infrastructure using Kubernetes' native capabilities.

## Architecture

The application consists of the following components:

1. **Frontend (React + Nginx)**: Serves the user interface for the e-commerce store.
2. **Backend (Node.js)**: Microservices handling APIs, user management, product inventory, orders, etc.
3. **MongoDB**: Stores product data, user information, and order details.
4. **RabbitMQ**: Used to handle asynchronous message processing, primarily for order management.

## Requirements

Before you begin, ensure you have the following installed:

- [Kubernetes Cluster](https://kubernetes.io/docs/tasks/tools/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/install-kubectl/)
- [Helm](https://helm.sh/) (optional, for easier chart management)
- A running Ingress Controller (e.g., Nginx Ingress Controller)
- Persistent Volume support in your cluster (for MongoDB and RabbitMQ)

## Project Structure

```bash
├── manifests
│   ├── frontend-deployment.yaml       # Frontend deployment and service
│   ├── backend-deployment.yaml        # Backend microservices deployment and service
│   ├── mongodb-statefulset.yaml       # MongoDB StatefulSet and service
│   ├── rabbitmq-statefulset.yaml      # RabbitMQ StatefulSet and service
│   ├── ingress.yaml                   # Ingress resource for exposing frontend and backend
│   └── hpa.yaml                       # Horizontal Pod Autoscaler for frontend and backend
├── config
│   ├── configmap.yaml                 # ConfigMaps for non-sensitive configuration
│   └── secrets.yaml                   # Secrets for sensitive data (e.g., MongoDB creds)
└── README.md                          # Project documentation


## Deployment Steps

### 1. Clone the Repository
Clone this repository to your local machine:

```bash
git clone https://github.com/your-repo/kubernetes-ecommerce-app.git
cd kubernetes-ecommerce-app

2. Apply Kubernetes Manifests

kubectl apply -f manifests/frontend-deployment.yaml
kubectl apply -f manifests/backend-deployment.yaml
kubectl apply -f manifests/mongodb-statefulset.yaml
kubectl apply -f manifests/rabbitmq-statefulset.yaml

3. Setup Ingress

kubectl apply -f manifests/ingress.yaml


4. Configure Secrets and ConfigMaps

kubectl apply -f config/configmap.yaml
kubectl apply -f config/secrets.yaml


5. Setup Horizontal Pod Autoscaling (HPA)

kubectl apply -f manifests/hpa.yaml


Monitoring and Autoscaling

helm install prometheus prometheus-community/kube-prometheus-stack



