# Kubernetes Pod Commands Cheat Sheet

## 1. Create / Apply a Pod
```bash
kubectl apply -f pod.yaml
kubectl run mypod --image=nginx
kubectl run mypod --image=nginx --port=80

**## 1. Get a Pod**
kubectl get pods
kubectl get pods -o wide
kubectl get pod mypod -o yaml
kubectl get pod mypod -o json
