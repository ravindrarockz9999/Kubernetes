# Kubernetes DaemonSet

A **DaemonSet** in Kubernetes ensures that **a copy of a specific Pod runs on all (or selected) nodes** in a cluster.  
It is commonly used for running **node-level services** such as logging, monitoring, or network agents.

---

## Key Concepts

- A **DaemonSet** guarantees that every node (or a subset of nodes) runs exactly **one Pod copy**.
- When **new nodes are added**, the DaemonSet automatically schedules Pods on them.
- When **nodes are removed**, the Pods on them are deleted.
- Useful for **cluster-wide services** that must run on every node.

---

## Common Use Cases

1. **Logging Agents**
   - Example: Fluentd, Logstash, or Filebeat on every node to collect logs.

2. **Monitoring Agents**
   - Example: Prometheus Node Exporter or Datadog Agent on every node for metrics.

3. **Networking Plugins**
   - Example: Calico or Weave Net, which require a Pod on each node.

4. **Custom Node-Level Services**
   - Example: Security scanning agents or custom scripts.

---

## DaemonSet vs Deployment

| Feature           | DaemonSet                          | Deployment                        |
|------------------|-----------------------------------|-----------------------------------|
| Pods per Node     | One Pod per node                   | Number of replicas defined by user |
| Node Addition     | Automatically schedules Pod on new nodes | Pods are scheduled based on replica count, may not cover all nodes |
| Use Case          | Node-level services (logging, monitoring) | Application workloads (frontend, backend) |

---

## Example: DaemonSet YAML

```yaml
apiVersion: apps/v1
kind: DaemonSet
metadata:
  name: node-monitor
  labels:
    app: node-monitor
spec:
  selector:
    matchLabels:
      app: node-monitor
  template:
    metadata:
      labels:
        app: node-monitor
    spec:
      containers:
      - name: monitor
        image: prom/node-exporter:latest
        ports:
        - containerPort: 9100
```
