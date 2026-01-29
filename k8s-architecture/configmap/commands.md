## Kubernetes ConfigMap Commands

### Create ConfigMaps
```yaml
kubectl create configmap <configmap-name> \
  --from-literal=key1=value1 \
  --from-literal=key2=value2

kubectl create configmap <configmap-name> \
  --from-literal=key=value \
  -n <namespace>                                                   # for namespace

kubectl apply -f configmap.yaml
```
### List ConfigMaps
```yaml
kubectl get configmaps
kubectl get cm                                 # cs is shortform of configmap
kubectl get configmaps -n <namespace>
kubectl describe configmap <configmap-name>
kubectl get configmap <configmap-name> -o yaml
```
### Edit ConfigMaps
```yaml
kubectl edit configmap <configmap-name>
kubectl replace -f configmap.yaml
```
### Delete ConfigMaps
```yaml
kubectl delete configmap <configmap-name>
kubectl delete configmap <configmap-name> -n <namespace>
kubectl delete configmaps --all -n <namespace>
