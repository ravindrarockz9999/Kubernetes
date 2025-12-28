# Kubernetes Deployment Commands

## 1. Create / Apply
```yaml
kubectl create -f deploy.yaml                                                                      # Declarative way to create
kubectl apply -f deploy.yaml                                                                       # Declarative way to create
kubectl create deployment <deployment-name> --image=<image-name>                                   # Imperative way to create
kubectl create deployment <deployment-name> --image=<image-name> --replicas=<number-of-replicas>   # Imperative way to create
kubectl create -f deploy.yaml -n <namespace-name>                                                  # create in particular namespace
```
## 2. List the Deployments
```yaml
kubectl get deploy
kubectl get deploy --show-labels                                                                 # To show the deployment labels
```
## 3. Describe the Deployments
```yaml
kubectl describe deployment <deployment-name>
```
## 4. Scale Deployment
```yaml
kubectl scale deployment <deployment-name> --replicas=<number-of-replicas>
```
## 5. Update Deployment (Change Image Version)
```yaml
kubectl set image deployment/<deployment-name> <container-name>=<new-image>:<tag>
```
## 6. Rollback deployement
```yaml
kubectl rollout undo deployment/<deployment-name>
kubectl rollout status deployment/<deployment-name>
kubectl rollout history deployment/<deployment-name>
```
## 7. Delete Deployment (Change Image Version)
```yaml
kubectl delete deployment <deployment-name>
kubectl delete --all deployment                                                                  # To delete all
kubectl delete --all deploy -n <namespace-name>                                                  # delete all in particular namespace
```
