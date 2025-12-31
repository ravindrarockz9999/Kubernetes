# Kubernetes Taints and Tolerations

In Kubernetes, **Taints and Tolerations** are mechanisms used to **control which Pods can be scheduled on which nodes**. They help ensure that certain workloads run only on specific nodes or avoid specific nodes.  

---

## 1. Taints

**Taints** are applied to **nodes** to repel Pods that do not tolerate them.  
- Think of a taint as a **“do not schedule unless tolerated”** marker on a node.

### Taint Format
**key=value:effect**

### Components
- **key:** A label key that describes the taint (e.g., `dedicated`, `gpu`)  
- **value:** Optional value describing the taint (e.g., `gpu=true`)  
- **effect:** What happens to Pods that **do not tolerate** the taint. Three possible values:
  1. `NoSchedule` – Pods that do not tolerate will **not be scheduled** on the node  
  2. `PreferNoSchedule` – Scheduler will **try to avoid** placing Pods on the node, but not guaranteed  
  3. `NoExecute` – Pods that do not tolerate will **be evicted** if already running on the node

## 2. Tolerations

In Kubernetes, **Tolerations** are applied to Pods to allow them to be scheduled on nodes that have **taints**.  
They are the counterpart to **taints**, which repel Pods from certain nodes.

## Key Components of a Toleration

| Field       | Description                                                                 |
|------------|-----------------------------------------------------------------------------|
| **key**    | The taint key the Pod can tolerate                                           |
| **operator** | Either `Equal` (matches key=value) or `Exists` (matches key only)          |
| **value**  | The taint value the Pod can tolerate (used with `Equal` operator)           |
| **effect** | The taint effect the Pod can tolerate: `NoSchedule`, `PreferNoSchedule`, `NoExecute` |
| **tolerationSeconds** | Optional: for `NoExecute` effect, how long the Pod tolerates before eviction |

---

### Summary

- Tolerations alone do not schedule Pods; they only allow them to ignore node taints.
- Combine with nodeSelector or affinity for precise scheduling.
- Common use cases: GPU nodes, dedicated workload nodes, maintenance/eviction scenarios.
