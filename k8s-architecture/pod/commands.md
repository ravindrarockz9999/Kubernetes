# Kubernetes Pod Commands

## 1. Create / Apply a Pod
```yaml
kubectl create -f pod.yaml                    # Declarative way to create
kubectl apply -f pod.yaml                     # Declarative way to create
kubectl run mypod --image=nginx               # Imperative way to create
kubectl run mypod --image=nginx --port=80     # Imperative way to create
```
## 2. List the Pods
```yaml
kubectl get pods
kubectl get pods --watch                      # Watch the pods in Real-Time
kubectl get pods -o wide                      # Shows extra info like node, Pod IP, and status
```
## 3. Describe the Pod
```yaml
kubectl describe pod <pod-name>
```
## 4. View Pod Logs
```yaml
kubectl logs <pod-name>
kubectl logs <pod-name> -c <container-name>   # To check init or sidecar container logs. 
```
## 5. Delete Pods
```yaml
kubectl delete pod <pod-name>                 # Delete one pod
kubectl delete pod --all                      # Delete all pods in the same namespace
```
## Advance commands

## 6. Manage Pods Labels
```yaml
kubectl label pod <pod-name> key=value        # Adds a new label (or updates an existing label) on the specified Pod.
kubectl get pods --show-labels                # show all labeles for all pods
```
## 7. Namespace-specific Commands
```yaml
kubectl get pods -n <namespace-name>
kubectl delete pod <pod-name> -n <namespace-name>
kubectl delete pod --all -n <namespace-name>
```
## 8. Forward Ports from Pod to Local
```yaml
kubectl port-forward <pod-name> 8080:80
```
## 9. Open a Terminal in a Pod
```yaml
kubectl exec -it <pod-name> -- bash            # To enter inside the Pod
```
## 10. Expose Pod via Service
```yaml
kubectl expose pod <pod-name> --type=NodePort --port=80
kubectl get svc
```
## 10. Apply Multiple YAML Files
```yaml
kubectl apply -f .                  # Apply all YAML files in the current directory (useful for multiple Pods or resources).
```
