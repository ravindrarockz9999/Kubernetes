# Kubernetes Autoscaling: HPA & VPA

Kubernetes provides built-in **autoscaling mechanisms** to help applications handle variable workloads efficiently. Two of the most important autoscaling features are:

- **Horizontal Pod Autoscaler (HPA)**
- **Vertical Pod Autoscaler (VPA)**

They solve different scaling problems and can be used independently or together (with care).

---

## Horizontal Pod Autoscaler (HPA)

### What is HPA?

The **Horizontal Pod Autoscaler (HPA)** automatically adjusts the **number of pod replicas** in a workload (Deployment, StatefulSet, etc.) based on observed metrics.

Instead of making pods bigger, HPA **adds or removes pods**.

---

### How HPA Works

1. HPA continuously monitors metrics such as:
   - CPU utilization
   - Memory utilization
   - Custom metrics (via Prometheus, etc.)
2. It compares current metrics against a **target value**.
3. Based on the result, it:
   - Scales **up** (adds more pods) when load increases
   - Scales **down** (removes pods) when load decreases

Metrics are collected via the **Metrics Server** or a custom metrics adapter.

---

### Common Use Cases for HPA

- Web applications with variable traffic
- APIs handling unpredictable request loads
- Microservices where scaling horizontally is easy and safe

---
### Pros of HPA

- Handles traffic spikes efficiently
- Improves availability and fault tolerance
- Ideal for stateless applications

---
### Limitations of HPA

- Cannot change CPU or memory limits of pods
- Scaling may lag during sudden traffic spikes
- Requires applications to support horizontal scaling
---

## Vertical Pod Autoscaler (VPA)

### What is VPA?
The Vertical Pod Autoscaler (VPA) automatically adjusts the CPU and memory requests/limits of containers.
Instead of adding pods, VPA resizes existing pods.

---

### How VPA Works

1. VPA monitors historical resource usage.
2. It calculates optimal CPU and memory values.
3. Depending on the mode:
   - Auto: Evicts pods and recreates them with new resource values
   - Initial: Sets resources only at pod creation
   - Off: Only provides recommendations
  
---
### Common Use Cases for VPA
- Applications with unpredictable memory usage
- Legacy apps that don’t scale horizontally well
- Jobs or batch workloads

---

### Pros of VPA

- Prevents under-provisioning and over-provisioning
- Optimizes cluster resource usage
- Reduces manual tuning of resource requests

---

### Limitations of VPA

- Pod restarts may cause brief downtime
- Not suitable for latency-sensitive apps
- Cannot safely scale pods horizontally at the same time (by default)

---

## HPA vs VPA Comparison

| Feature | Horizontal Pod Autoscaler (HPA) | Vertical Pod Autoscaler (VPA) |
|-------|---------------------------------|-------------------------------|
| Scaling Direction | Horizontal (adds/removes pods) | Vertical (resizes pod resources) |
| What It Scales | Number of pod replicas | CPU and memory requests/limits |
| Pod Restart Required | ❌ No | ✅ Yes (in Auto mode) |
| Scaling Trigger | CPU, memory, or custom metrics | Historical resource usage |
| Best Suited For | Stateless, horizontally scalable apps | Apps with unpredictable resource usage |
| Handles Traffic Spikes | ✅ Very well | ❌ Limited |
| Resource Optimization | ❌ Limited | ✅ Excellent |
| Risk of Downtime | ❌ Low | ⚠️ Possible during pod restarts |
| Configuration Complexity | Simple | Moderate |
| Production Readiness | Widely used | Use with caution |
| Common Workloads | Web apps, APIs, microservices | Batch jobs, legacy apps |
| Metrics Source | Metrics Server / Prometheus | VPA recommender |
| Works with Stateful Apps | ⚠️ Limited | ⚠️ Limited |
| Can Be Used Together | ⚠️ With restrictions | ⚠️ With restrictions |

---

### Key Differences Summary

- **HPA** increases or decreases the **number of pods**
- **VPA** increases or decreases the **size of pods**
- HPA is ideal for **traffic-based scaling**
- VPA is ideal for **resource optimization**
- Using both together requires careful configuration to avoid conflicts

---

### Recommendation

- Use **HPA** for:
  - Web applications
  - Microservices
  - High-traffic systems

- Use **VPA** for:
  - Batch jobs
  - Memory-heavy applications
  - Legacy workloads

- Avoid running both in **full auto mode** simultaneously

---

### Summary

- HPA scales the number of pods
- VPA scales the size of pods
- Choose HPA for traffic spikes
- Choose VPA for unpredictable resource usage
- Combine carefully if needed
