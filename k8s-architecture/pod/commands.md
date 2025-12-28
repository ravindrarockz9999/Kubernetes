## Kubernetes Pod Commands

# 1. Create / Apply a Pod
```yaml
kubectl create -f pod.yaml
kubectl apply -f pod.yaml
kubectl run mypod --image=nginx
kubectl run mypod --image=nginx --port=80
```
# 2. List the Pods
```yaml
kubectl get pods
kubectl get pods -o wide   # Shows extra info like node, Pod IP, and status
```
