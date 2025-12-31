# Kubernetes Labels and Selectors

In Kubernetes, **Labels** and **Selectors** are used to organize, identify, and manage resources such as Pods, Services, and Deployments.

---

## Labels

**Labels** are key-value pairs attached to Kubernetes objects.

- **Purpose:** To organize and categorize resources.
- **Format:** `key: value`
- **Attached to:** Pods, Services, Deployments, Nodes, etc.

**Example:**
```yaml
metadata:
  name: frontend-pod
  labels:
    app: frontend
    environment: production
```
### app=frontend → identifies the application
### environment=production → identifies the environment

## Selectors

In Kubernetes, **Selectors** are used to **query and select resources** based on their **labels**. They allow objects like Services, Deployments, and ReplicaSets to dynamically identify and manage the right set of Pods.

---

## Types of Selectors

### 1. Equality-based Selectors
- Matches resources where a label **equals** or **does not equal** a value.
- Operators: `=`, `==`, `!=`

**Example:**
```yaml
selector:
  matchLabels:
    app: frontend
```
- Selects all Pods with the label app=frontend.
### 2 . Set-based Selectors
- Matches resources where a label is in a set or is not in a set.
- Operators: In, NotIn, Exists, DoesNotExist

**Example**
```yaml
selector:
  matchExpressions:
    - key: environment
      operator: In
      values: ["production", "staging"]
```
- Selects all Pods with the environment label set to either production or staging.

## Common Use Cases

- Services: Select Pods to route traffic
- Deployments: Select Pods to manage replicas
- Jobs/CronJobs: Select Pods to perform specific tasks

## Summary

- Selectors are the way Kubernetes matches resources based on labels.
- They allow dynamic management of Pods by Services, Deployments, and other controllers.
- Two main types: Equality-based and Set-based.
