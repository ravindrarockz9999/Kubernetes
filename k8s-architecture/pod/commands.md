# List pods
kubectl get pods
kubectl get pods -A
kubectl get pods -o wide
kubectl get pods --watch

# Describe pod
kubectl describe pod <pod-name>

# Get pod logs
kubectl logs <pod-name>
kubectl logs -f <pod-name>  # Follow logs
kubectl logs <pod-name> -c <container-name>  # Multi-container pod

# Execute command in pod
kubectl exec -it <pod-name> -- /bin/bash
kubectl exec <pod-name> -- <command>

# Delete pod
kubectl delete pod <pod-name>

# Port forward
kubectl port-forward <pod-name> <local-port>:<pod-port>
