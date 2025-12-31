# Kubernetes node commands

## 1. View All Nodes

```bash
kubectl get nodes
kubectl get nodes -o wide       # To see IP address,etc..
```

## 2. Describe node

```yaml
kubectl describe node <node-name>
```
## 3. Node Labels
```yaml
kubectl label nodes <node-name> <key>=<value>   # craete node label 
kubectl label nodes <node-name> <key>-          # To remove node label just give key '-'
kubectl get nodes --show-labels                 # Show all labels on all nodes
```
