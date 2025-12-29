# Kubernetes Namespace Commands:
## 1. Creating a Namespace
### Imperative
```bash
kubectl create namespace dev
kubectl create ns prod                   # ns is shotform of namespace
``` 
### Declarative
```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: dev
```
## 2. Using a Namespace

Create a resource in a specific namespace:

```bash
kubectl run nginx --image=nginx --namespace=dev
kubectl run nginx --image=nginx -n dev                # In short is -n for namespace
```

## 3. Get and Describe namespace:

```bash
kubectl get ns
kubectl get pods -n <namespace-name>
kubectl get deployments --namespace=prod
kubectl describe namespace dev
kubectl get pods --all-namespaces                      # Get all pod resources for all namespaces
kubectl get all -n <namespace-name>                    # Get all resources
```
## 4. Delete a Namespace
```bash
kubectl delete namespace dev
kubectl delete ns dev
### Note: Delete all the resources first before deleting any namespace.
```
## 5. Labels in Namespace
```bash
kubectl label namespace dev env=development           # Add the Label
kubectl label namespace dev env-                      # Remove the Label
```
## 6. Set Default Namespace (Current Context)
```bash
kubectl config set-context --current --namespace=dev
kubectl config view --minify | grep namespace               # check current context
kubectl config set-context --current --namespace=default    # Switch back to default namespace
```
