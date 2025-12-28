# Kubernetes Pod – Simple Explanation

Here we learn about a **Kubernetes Pod**, what it is, how it works, and how to create and manage it using basic Kubernetes commands.

---

## What is a Pod?

A **Pod** is the **smallest unit in Kubernetes**.  
It is a wrapper around one or more containers (like Docker) that run together on the same node.

Think of a Pod as a **single application instance**.

---

## Key Features of a Pod

- Runs **one or more containers** together
- Containers share:
  - Network (IP address, port)
  - Storage volumes
- Pods are **ephemeral** (temporary) – if a Pod dies, Kubernetes can create a new one

---

## Pod Components

1. **Containers**
   - The actual application(s) running inside the Pod
   - Examples: Nginx, Python app, Node.js app

2. **Shared Network**
   - All containers in a Pod share the same IP and ports

3. **Shared Storage**
   - Containers in a Pod can access the same volumes for persistent data

4. **Labels**
   - Key-value pairs used to identify and manage Pods
   - Example: `app=web`

---

## Example Pod YAML

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-first-pod
  labels:
    app: web
spec:
  containers:
  - name: nginx-container
    image: nginx:latest
    ports:
    - containerPort: 80

