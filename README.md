# Istio gRPC with Minikube (Golang)

This project demonstrates a simple implementation of **gRPC** with **Istio Service Mesh** on a local **Minikube** Kubernetes cluster. Applications are containerized using Docker, and Istio is used as a gateway and load balancer.

---

## ✅ Prerequisites
- **Go compiler** installed
- **Operating System:** Windows 10 (with WSL2)
- **Minikube version:** v1.19.0
- **Docker Desktop version:** 3.3.2 (Engine: v20.10.5)
- **Istio version:** 1.9.4

---

## 🚀 Setup Guide (10 Steps)

### Step 1: Enable WSL2
Install and enable Windows Subsystem for Linux (WSL2):  
🔗 [WSL2 Setup Guide](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

### Step 2: Install Docker Desktop for Windows
- Open Docker Dashboard → Settings → Enable WSL2 integration
- Ensure Ubuntu is selected/enabled

### Step 3: Set Up Ubuntu
- Install Ubuntu from Microsoft Store
- Launch Ubuntu and complete initial setup

### Step 4: Clone the Repository
- Clone or download this repository
- Navigate to the project folder in WSL terminal via VSCode or command line:
```bash
cd /path/to/project
wsl
```

### Step 5: Install Minikube
Run these commands in the WSL terminal:
```bash
curl -LO https://storage.googleapis.com/minikube/releases/latest/minikube-linux-amd64
sudo install minikube-linux-amd64 /usr/local/bin/minikube
```
Set the driver to Docker:
```bash
minikube config set driver docker
```
Start the Kubernetes cluster:
```bash
minikube start --memory=4096 --cpus=4
```

### Step 6: Install Istio (Demo Profile)
Follow steps 1–5 here:  
🔗 [Istio Getting Started Guide](https://istio.io/latest/docs/setup/getting-started/)

Add a namespace label for automatic Envoy sidecar injection:
```bash
kubectl label namespace default istio-injection=enabled
```

### Step 7: Copy Istio YAML Files
- Copy the `istio-yaml/` folder from this repo into the `istio-1.9.4` directory (or your version)

### Step 8: Deploy Application to Cluster
Run from within the `istio-1.9.4` directory:
```bash
kubectl apply -f istio-yaml/grpc.yaml
```
Check pod status:
```bash
kubectl get pods
```

### Step 9: Start Minikube Tunnel
Run this in a new terminal (keep it running):
```bash
minikube tunnel
```

### Step 10: Run the gRPC Client
In a new terminal, run:
```bash
go run client.go
```

---

## 🎉 Result
You’ve successfully set up **Istio Service Mesh** with **gRPC** and **Minikube** on your local Windows machine!

---

## 📁 Project Structure
```
├── client.go
├── server.go
├── proto/
├── Dockerfile
├── istio-yaml/
└── README.md
```

---

## 📌 Notes
- Replace version numbers according to your installed versions
- Ensure Docker and Minikube are correctly communicating
- Minikube tunnel must remain running for the service to be accessible

---

## 📬 Questions?
Feel free to open an issue or PR for improvements!

