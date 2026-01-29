# Kubernetes Secrets

## What is a Secret in Kubernetes?

A **Secret** in Kubernetes is an object used to **store and manage sensitive information** such as:

- Passwords
- API keys
- Tokens
- Certificates
- SSH keys

Secrets help keep sensitive data **separate from application code and container images**.

> ⚠️ Secrets are **not encrypted by default** (they are Base64 encoded).  
> Proper cluster security is required for true protection.

---

## Why Use Secrets?

Without Secrets:
- Sensitive data may be hardcoded in YAML files
- Secrets may be exposed in Git repositories
- Changing credentials requires rebuilding images

With Secrets:
- Sensitive data is stored securely
- Easier rotation of credentials
- Better separation of concerns
- Same image can be used across environments

---

## How Kubernetes Secrets Work

1. Sensitive data is stored in a Secret object.
2. Pods reference the Secret.
3. Kubernetes injects the Secret into the container as:
   - Environment variables
   - Files inside the container
   - Image pull credentials

---

## Types of Kubernetes Secrets

### 1. Opaque (Generic Secret)

The most commonly used Secret type.

Used for:
- Passwords
- API tokens
- Custom credentials
---
### 2. Docker Registry Secret

Used to authenticate with private container registries.

```yaml
type: kubernetes.io/dockerconfigjson
```
#### Use case:
- Pulling images from private Docker registries
---
### 3. TLS Secret

Used to store TLS certificates and private keys.
```yaml
type: kubernetes.io/tls
```
#### Use case:
- HTTPS
- Ingress TLS configuration
---
### 4. Service Account Token Secret

Automatically created by Kubernetes.

#### Use case:
- Pod authentication with Kubernetes API

---

### Best Practices

- Never store Secrets in Git repositories
- Use RBAC to restrict Secret access
- Enable encryption at rest
- Rotate Secrets regularly
- Use external secret managers for production
---
### Limitations of Secrets

- Base64 encoding is not encryption
- Can be exposed if RBAC is misconfigured
- Still visible to users with cluster access
---
### Summary

- Secrets store sensitive information
- Can be injected as env vars or files
- More secure than ConfigMaps
- Essential for production workloads
---
## ConfigMap vs Secret: 

| Feature | ConfigMap | Secret |
|---------|-----------|--------|
| Purpose | Store **non-sensitive configuration** | Store **sensitive information** (passwords, keys, tokens) |
| Data Storage | Plain text | Base64 encoded (can be encrypted at rest) |
| Examples | App settings, URLs, feature flags | Database passwords, API keys, TLS certificates |
| Use Case | Non-sensitive environment variables or config files | Credentials and sensitive data |
| Injection into Pods | Env variables, files, command args | Env variables, files, image pull secrets |
| Security | Low | Higher (requires RBAC, can be encrypted) |
| Required for Production? | Optional | Recommended for anything sensitive |

**Key Takeaway:**  
- Use **ConfigMap** for normal configuration.  
- Use **Secret** for anything sensitive.  

---
