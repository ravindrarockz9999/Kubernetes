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
```

## Kubernetes Static Pod

A **Static Pod** is a special type of Pod in Kubernetes that is **managed directly by the kubelet on a specific node**, rather than by the API server or a controller like Deployment or ReplicaSet.  

Static pods are mainly used for **critical system components**, such as the Kubernetes control plane (`kube-apiserver`, `kube-scheduler`, `kube-controller-manager`).

---

## Key Features

- **Node-specific:** Runs on the node where the manifest file is placed.
- **Managed by kubelet:** The kubelet watches a directory (usually `/etc/kubernetes/manifests`) for static pod manifests and creates pods automatically.
- **No controllers:** Static pods are **not managed by Deployment, ReplicaSet, or StatefulSet**.
- **Immutable via API:** To update, modify the YAML file on the node directly.
- **System components:** Often used for control-plane components or critical node-level services.

---

## Static Pod Manifest Example

Create a file `/etc/kubernetes/manifests/static-pod.yaml`:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: my-static-pod
spec:
  containers:
  - name: nginx
    image: nginx:latest
    ports:
      - containerPort: 80
```
# Difference Between Static Pods and Regular Pods in Kubernetes

This table summarizes the **key differences** between **Static Pods** and **Regular Pods** in Kubernetes.

| Feature           | Static Pod                               | Regular Pod                               |
|------------------|-----------------------------------------|------------------------------------------|
| **Managed By**    | Kubelet on the node                       | Kubernetes API server / Controllers (Deployment, ReplicaSet, StatefulSet) |
| **Controllers**   | ❌ Not controlled by any controller       | ✅ Managed by controllers                 |
| **Creation**      | Created from **local YAML files** on the node (`/etc/kubernetes/manifests`) | Created via `kubectl` or controllers through the API server |
| **Namespace**     | Default (usually)                         | Any namespace                             |
| **Lifecycle**     | Tied to the kubelet; Pod exists as long as YAML file exists | Managed by controller; can be scaled, updated, or deleted |
| **Use Case**      | Critical node-level components (e.g., `kube-apiserver`, `kube-scheduler`) | Normal applications or workloads        |
| **API Server Visibility** | Appears in API server as a **mirror pod** | Fully managed and tracked by API server |

---

## Summary

- **Static Pods:** Node-specific, kubelet-managed, used for critical system components.  
- **Regular Pods:** API-server managed, scalable, and controlled by controllers for normal workloads.  
