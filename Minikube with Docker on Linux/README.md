# Minikube with Docker on Linux ☮️

## What is Minikube?

Minikube is a tool that helps you run a local Kubernetes cluster on your machine. It's perfect for developers who want to experiment with Kubernetes without setting up a large cloud infrastructure. Minikube provides a simple way to start a Kubernetes cluster on a local machine, and it works with various drivers like Docker, KVM, and VirtualBox.

Minikube makes Kubernetes accessible for local development, testing, and experimentation. It simplifies the process of deploying and managing Kubernetes clusters locally without the need for extensive resources.

## What is Kubernetes? ☮️

Kubernetes is an open-source platform for automating the deployment, scaling, and management of containerized applications. It orchestrates and manages containers (such as those created with Docker) to ensure that applications run reliably and efficiently, whether in a development, test, or production environment.

Kubernetes allows you to:

- Deploy applications in containers across clusters.
- Scale applications up or down with ease.
- Manage containerized workloads with minimal effort.
- Ensure high availability, load balancing, and fault tolerance for your applications.

By using Kubernetes, developers can focus on writing code and let Kubernetes manage the complexity of application deployment and scaling.

## ✅ Step 1: Install Required Tools

Before starting, ensure you have the necessary software installed.

### 1. Install Docker Engine 🐋

Minikube can run Kubernetes inside a Docker container, so install Docker:

```sh
sudo apt update
sudo apt install -y docker.io
```

Enable and start Docker:

```sh
sudo systemctl enable --now docker
```

Add your user to the Docker group (log out and back in after this):

```sh
sudo usermod -aG docker $USER
```

Verify Docker installation:

```sh
docker --version
```

### 2. Install Minikube 🛆

Download and install Minikube:

```sh
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```

Verify installation:

```sh
minikube version
```

### 3. Install kubectl

```sh
curl -LO "https://dl.k8s.io/release/$(curl -L -s https://dl.k8s.io/release/stable.txt)/bin/linux/amd64/kubectl"
sudo install kubectl /usr/local/bin/kubectl
```

Verify installation:

```sh
kubectl version --client
```

## ✅ Step 2: Start Minikube with Docker Driver 🐳

Now, start Minikube using Docker as the driver. Ensure that your Docker Engine is running in the background.

```sh
minikube start --driver=docker
```

Check the status:

```sh
minikube status
```

## ✅ Step 3: Deploy an Application 🚀

Deploy a simple application (nginx).

### 1. Create an Nginx Deployment

```sh
kubectl create deployment nginx --image=nginx
```

### 2. Expose the Deployment 🔒

```sh
kubectl expose deployment nginx --type=NodePort --port=80
```

### 3. Get the Service URL 🔗

```sh
minikube service nginx --url
```

Open the URL in your browser to see the running nginx web server. 🌐

## ✅ Step 4: Manage Kubernetes Cluster

### 1. Check Running Pods 🗋

```sh
kubectl get pods
```

### 2. Scale the Deployment 📏

Scale to 3 replicas:

```sh
kubectl scale deployment nginx --replicas=3
```

Check pods again:

```sh
kubectl get pods
```

### 3. Delete the Deployment 🪣

```sh
kubectl delete service nginx
kubectl delete deployment nginx
```

## ✅ Step 5: Stop and Delete Minikube 🛢️

### 1. Stop Minikube

```sh
minikube stop
```

### 2. Delete the Cluster

```sh
minikube delete
```

This removes all Kubernetes resources.

## 🎡 Conclusion

By using Minikube with Docker on Linux, you can run Kubernetes locally without needing a virtual machine. Docker provides an easy way to manage your cluster and experiment with Kubernetes.

