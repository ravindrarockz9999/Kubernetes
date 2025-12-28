# Kubernetes Pod Commands Reference

## Create & Run Pods through imperative way
kubectl run mypod --image=nginx
kubectl run mypod --image=nginx --restart=Never
kubectl run mypod --image=nginx --port=80

## Get Pods
kubectl get pods
kubectl get pods -o wide
kubectl get pod mypod -o yaml
kubectl get pod mypod -o json

## Describe Pods
kubectl describe pod mypod

## Delete Pods
kubectl delete pod mypod
kubectl delete pod mypod --grace-period=0 --force

## Logs
kubectl logs mypod
kubectl logs -f mypod
kubectl logs mypod -c mycontainer

## Exec into Pods
kubectl exec -it mypod -- /bin/bash
kubectl exec -it mypod -- /bin/sh
kubectl exec mypod -- ls /app

## Port Forwarding
kubectl port-forward pod/mypod 8080:80

## Pod Status & Events
kubectl get pod mypod -o yaml | grep -i phase
kubectl get events --field-selector involvedObject.name=mypod

## Apply Pod YAML for declarative way
kubectl apply -f pod.yaml
kubectl delete -f pod.yaml

## Debugging Pods
kubectl debug mypod -it --image=busybox
kubectl attach mypod -c mycontainer

## Namespace Targeting
kubectl get pods -n mynamespace
kubectl describe pod mypod -n mynamespace
kubectl delete pod mypod -n mynamespace

## Dry Run & Output
kubectl run testpod --image=nginx --dry-run=client -o yaml
kubectl get pod mypod -o yaml > mypod.yaml

## Label & Annotate Pods
kubectl label pod mypod env=dev
kubectl annotate pod mypod description="Test pod"

## Resource Usage
kubectl top pod
kubectl top pod mypod
