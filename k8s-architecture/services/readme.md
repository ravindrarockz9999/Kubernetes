# Kubernetes Service

## 📌 What is a Service in Kubernetes?

A Service is a stable way to access a group of Pods.
Pods can be created, destroyed, or get new IP addresses. A Service gives them one fixed name and IP so other parts of your app can reliably talk to them.

### Why Services Are Needed
- Pods are **ephemeral** (they can be created, destroyed, or replaced)
- Pod IP addresses **change frequently**
- Services provide:
  - Stable IP and DNS name
  - Load balancing
  - Service discovery
  - Decoupling between Pods and clients

👉 **In short:**  
A Kubernetes Service allows applications to communicate reliably with Pods.

---

## 🧠 How Kubernetes Service Works

1. Pods are created with labels
2. A Service selects Pods using **label selectors**
3. The Service exposes a **virtual IP (Cluster IP)**
4. Traffic sent to the Service is **load-balanced** across matching Pods


---

## 🧩 Service Components

| Component | Description |
|---------|-------------|
| Selector | Matches Pods using labels |
| Port | Port exposed by the Service |
| TargetPort | Port on the Pod |
| ClusterIP | Internal IP assigned to the Service |
| Endpoints | Actual Pod IPs behind the Service |

---

## 🔢 Types of Kubernetes Services

Kubernetes supports **5 main types** of Services:

---

## 1️⃣ ClusterIP (Default)

### Description
- Exposes the Service **inside the cluster only**
- Not accessible from outside the cluster
- Used for **internal communication**

### Use Case
- Backend services
- Internal APIs
- Microservice-to-microservice communication

## 2️⃣ NodePort

### Description
- Used for **internal communication**
- Exposes the Service on each Node’s IP
- Uses a static port (30000–32767)
- Accessible externally

### Use Case
- Development
- Testing
- Simple external access

## 3️⃣ LoadBalancer
### Description

- Creates an external load balancer
- Works with cloud providers (AWS, GCP, Azure)
- Automatically assigns a public IP

### Use Case

- Production applications
- Public-facing services

## 4️⃣ ExternalName
### Description

- Maps a Service to an external DNS name
- No selectors or Pods involved
- Acts as a DNS alias

### Use Case
- Access external services (e.g., databases, APIs)
- Migration scenarios

## 5️⃣ Headless Service
### Description

- No ClusterIP (clusterIP: None)
- Direct access to Pod IPs
- No load balancing

### Use Case

- Databases (MongoDB, Cassandra)
- Stateful applications
- Custom load balancing
Conclusion

## ✅ Best Practices

- Use ClusterIP for internal services
- Use LoadBalancer for production external access
- Avoid NodePort in production
- Use Headless Services for StatefulSets
- Always use labels consistently

### All Kubernetes Service type YAML files are available in the examples/ folder
