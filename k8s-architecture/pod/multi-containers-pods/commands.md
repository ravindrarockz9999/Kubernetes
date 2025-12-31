## Kubernetes Multi Container Pod Commands:

### List out the containers inside pods
```yaml
kubectl get pod <pod-name> -o jsonpath='{.spec.containers[*].name}'
kubectl get pod <pod-name> -o jsonpath='{.spec.initContainers[*].name}'   # List init containers in pod
```

### Execute into specific container
```yaml
kubectl exec -it <pod-name> -c <container-name> -- sh                    # Init or sidecar to execute
```
### View logs of specific container
```yaml
kubectl logs <pod-name> -c <container-name>                              # Init or Sidecar logs 
```
