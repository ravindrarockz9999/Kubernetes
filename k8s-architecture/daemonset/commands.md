# Kubernetes DaemonSet Commands

## 1. Create DaemonSet
```yaml
kubectl apply -f daemonset.yaml
```
## 2. Get all DaemonSets
```yaml
kubectl get daemonsets
kubectl get ds                    # Both are same ds is shorcut of daemonsets
```
## 3. Describe DaemonSet
```yaml
kubectl describe daemonset <ds-name>
```
## 4. Delete DaemonSet
```yaml
kubectl delete daemonset <ds-name>
```
