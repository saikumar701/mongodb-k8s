# 🚀 MongoDB + Mongo Express on Kubernetes (Minikube Setup)

This project demonstrates how to deploy **MongoDB** and **Mongo Express** using **Docker** and **Kubernetes** with **Minikube** on a local machine — **without using AWS or Azure**.

---

## 💻 Kubernetes Commands

- `minikube start`  
  Starts the Minikube cluster

- `kubectl apply -f .`  
  Applies all YAML files in the current folder

- `kubectl get pods`  
  Displays all running pods, their status, and image info

- `kubectl get svc`  
  Lists all services running in Minikube

- `minikube service service-name`  
  Opens the specified service in the browser (e.g., `mongo-express`)

- `kubectl delete all --all`  
  Deletes all deployments, services, pods, etc. (full cleanup)

---

## 📁 Project Structure

k8s-mongodb/
│
├── mongo-app.yaml # MongoDB Deployment + Service
├── web-app.yaml # Mongo Express Deployment + Service
├── mongo-config.yaml # ConfigMap with Mongo host details
├── secret.yaml # Secret with Mongo credentials (Base64 encoded)
└── README.md # Project guide and commands


---

## 🔧 Prerequisites

Make sure the following are installed:

- [Docker](https://www.docker.com/)
- [Minikube](https://minikube.sigs.k8s.io/docs/start/)
- [kubectl](https://kubernetes.io/docs/tasks/tools/)
- [Chocolatey (Windows users)](https://chocolatey.org/install)

Install Minikube via CLI (Windows):

```bash
choco install minikube -y
# Pulling images from Docker Hub
docker pull mongo
docker pull mongo-express

# Build a custom image (optional)
docker build -t my-mongo-express .

# Tagging a Docker image
docker tag my-mongo-express sai701/mongo-express:latest

# Login to Docker Hub
docker login

# Pushing image to Docker Hub
docker push sai701/mongo-express:latest

# List Docker images
docker images

# Remove Docker image
docker rmi <image_id>

# Start Minikube cluster
minikube start

# Apply all Kubernetes YAML files in the directory
kubectl apply -f .

# Check the status of all pods
kubectl get pods

# List all running services and their ports
kubectl get svc

# Access a particular service in the browser
minikube service mongo-express

# Delete all Kubernetes resources
kubectl delete all --all
