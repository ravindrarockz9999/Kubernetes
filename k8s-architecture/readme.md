# Kubernetes Architecture – Simple Explanation

This repository explains **Kubernetes (K8s) architecture** in a simple and easy way.

Kubernetes is a system that helps you **run, manage, and scale applications** using containers (like Docker).

---
![Kubernetes Architecture](k8s-architecture/k8s.png)
## What is Kubernetes?
Kubernetes is an **orchestration tool** that:
- Runs applications in containers
- Automatically heals failed containers
- Scales applications up or down
- Manages networking and storage

---

## High-Level Kubernetes Architecture

Kubernetes has **two main parts**:

1. **Control Plane (Master Node)**
2. **Worker Nodes**

---

## 1. Control Plane (Master Node)

The Control Plane is the **brain of Kubernetes**.  
It decides **what should run and where**.

### Main Components:

### 🔹 API Server
- Entry point of Kubernetes
- All commands (`kubectl`) go through this
- Communicates with all components

### 🔹 etcd
- Key-value database
- Stores **cluster state**
- Example: what pods are running, configs, secrets

### 🔹 Scheduler
- Decides **which pod runs on which node**
- Chooses the best worker node

### 🔹 Controller Manager
- Watches the cluster
- Fixes problems automatically
- Example: restarts pods if they fail

---

## 2. Worker Nodes

Worker nodes are where **your application actually runs**.

### Main Components:

### 🔹 Kubelet
- Agent running on each worker node
- Talks to API Server
- Makes sure containers are running

### 🔹 Container Runtime
- Runs containers
- Examples: Docker, containerd, CRI-O

### 🔹 Kube Proxy
- Handles networking
- Allows pods to communicate
- Manages service traffic

---

## Kubernetes Objects (Basic Building Blocks)

### 📦 Pod
- Smallest unit in Kubernetes
- Runs one or more containers

### 🚀 Deployment
- Manages pods
- Handles scaling and updates

### 🌐 Service
- Exposes pods inside or outside cluster
- Provides stable networking

### 🌍 Ingress
- Manages external HTTP/HTTPS access
- Routes traffic to services

### ⚙️ ConfigMap
- Stores application configuration

### 🔐 Secret
- Stores sensitive data (passwords, tokens)

---

## Simple Workflow (How Kubernetes Works)

1. User runs `kubectl apply`
2. Request goes to **API Server**
3. Data is stored in **etcd**
4. **Scheduler** selects a worker node
5. **Kubelet** starts the container
6. **Service / Ingress** exposes the app

---

## Why Kubernetes is Used?
- Automatic healing
- Easy scaling
- High availability
- Platform independent
- Production-ready

---

## Conclusion
Kubernetes helps you **deploy, manage, and scale applications automatically** using a strong architecture with control plane and worker nodes.

This architecture makes applications **reliable, scalable, and fault-tolerant**.
