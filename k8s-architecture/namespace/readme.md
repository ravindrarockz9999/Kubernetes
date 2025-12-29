# Kubernetes Namespace

## What is a Namespace in Kubernetes?

A **Namespace** in Kubernetes is a **logical partition** within a cluster that helps organize, isolate, and manage resources.

> **Simple definition:**
> A Namespace is like a department in a company, where each department has its own team, projects, and resources, but all are part of the same organization.

---

## Why Do We Need Namespaces?

Namespaces help solve several problems in Kubernetes clusters:

* Organize resources in large clusters
* Avoid naming conflicts between resources
* Separate environments (dev, test, prod)
* Apply access control and resource limits
* Enable multiple teams to share one cluster safely

---

## Key Characteristics

* A Kubernetes cluster can contain **multiple namespaces**
* Resources inside one namespace are **isolated** from others
* Resource names must be **unique within a namespace**
* Namespaces are especially useful in **production and multi-team setups**

---

## Default Namespaces in Kubernetes

Kubernetes creates the following namespaces automatically:

| Namespace         | Description                         |
| ----------------- | ----------------------------------- |
| `default`         | Used when no namespace is specified |
| `kube-system`     | Kubernetes system components        |
| `kube-public`     | Publicly readable resources         |
| `kube-node-lease` | Node heartbeat and lease objects    |

---

## Namespaced vs Cluster-Wide Resources

### Namespaced Resources

These exist **inside a namespace**:

* Pods
* Services
* Deployments
* ReplicaSets
* ConfigMaps
* Secrets

### Cluster-Wide Resources

These exist **across the entire cluster**:

* Nodes
* PersistentVolumes
* Namespaces

---

## Example Use Case

One Kubernetes cluster shared by multiple environments:

```
dev
testing
prod
```

Each namespace can have:

* Its own applications
* Its own configuration
* Its own secrets and services

Resources in one namespace do not affect others.

---

## Creating a Namespace

```bash
kubectl create namespace dev
```

---

## Using a Namespace

Create a resource in a specific namespace:

```bash
kubectl run nginx --image=nginx --namespace=dev
```

List Pods in a namespace:

```bash
kubectl get pods -n dev
```

---

## Resource Quotas and Limits

Namespaces support **resource quotas**, allowing you to:

* Limit CPU and memory usage
* Control the number of Pods, Services, etc.

This prevents one namespace from consuming all cluster resources.

---

## Access Control with RBAC

Namespaces work with **Role-Based Access Control (RBAC)** to manage permissions:

* Users can be restricted to specific namespaces
* Teams can only access their own namespace
* Administrators can access all namespaces

---

## When to Use Namespaces

### Recommended:

* Multiple teams sharing a cluster
* Multiple environments (dev, staging, prod)
* Production Kubernetes clusters

### Not Required:

* Very small or single-user clusters
* Local testing with minimal resources

---

## Conclusion

* Namespace provides logical isolation in Kubernetes
* Helps with organization, security, and resource management
* Essential for scalable and production-ready Kubernetes clusters

---

## References

* Kubernetes Official Documentation
* kubectl CLI Reference
