# Kubernetes: ReplicationController vs ReplicaSet

In Kubernetes, both **ReplicationController (RC)** and **ReplicaSet (RS)** are used to ensure that a specified number of pod replicas are running at any given time. They help maintain high availability and scalability of applications.

---

## ReplicationController (RC)

A **ReplicationController** ensures that a certain number of pod replicas are always running. If a pod fails or is deleted, the RC creates a new pod to maintain the desired number.

### Key Points
- Legacy Kubernetes object (older version).  
- Ensures **exact number of pod replicas** are running.  
- Uses **exact-match selectors** to identify pods.  
- Usually replaced by ReplicaSet in modern Kubernetes.

---

## ReplicaSet (RS)

A **ReplicaSet** is the newer version of a ReplicationController with additional features. It ensures that a specified number of pod replicas are running, just like RC, but supports more advanced selectors.

### Key Points
- Modern replacement for ReplicationController.  
- Supports **set-based selectors** (`matchLabels` and `matchExpressions`).  
- Usually **managed by a Deployment** rather than directly.  
- Maintains desired pod replicas automatically.

---

## Quick Differences: RC vs RS

| Feature                  | ReplicationController (RC)       | ReplicaSet (RS)                |
|--------------------------|---------------------------------|--------------------------------|
| API Version              | v1                               | apps/v1                        |
| Selector Type            | Exact match only                 | Exact + set-based               |
| Modern Usage             | Legacy / backward-compatible     | Preferred, often via Deployment|
| Pod Management           | Maintains pod replicas           | Maintains pod replicas         |
| Deployment Support       | Not required                     | Typically used by Deployments  |

---

## Summary

- Use **ReplicaSet** in modern Kubernetes clusters.  
- **ReplicationController** is mainly for legacy support.  
- Both help in scaling and ensuring pods are always running.

