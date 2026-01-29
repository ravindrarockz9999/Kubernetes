## Kubernetes commands hpa/vpa

### HPA Prerequisites
```yaml
kubectl get deployment metrics-server -n kube-system      # Check metrics is installed
```
### VPA Prerequisites
```yaml
kubectl get crd | grep verticalpodautoscaler              # Check VPA (install seperately with CRDs)
```
### Create hpa
```yaml
kubectl autoscale deployment <deployment-name> \
  --cpu-percent=50 \
  --min=1 \
  --max=10

kubectl autoscale deployment <deployment-name> \
  --cpu-percent=60 \
  --min=2 \
  --max=8 \
  -n <namespace>

kubectl autoscale deployment <deployment-name> \
  --cpu-percent=50 \
  --min=1 \
  --max=10 \
  --dry-run=client -o yaml                            # Generate yaml file

kubectl apply -f hpa.yaml
```

### List hpa/vpa
```yaml
kubectl get hpa
kubectl get vpa
kubectl get hpa -n <namespace>
kubectl get vpa -n <namespace>
kubectl describe hpa <hpa-name>
kubectl describe vpa <vpa-name>
kubectl get hpa <hpa-name> -o yaml      # Get hpa as yaml
kubectl get vpa <vpa-name> -o yaml      # Get vpa as yaml
```
### Edit hpa/vpa
```yaml
kubectl edit hpa <hpa-name>
kubectl edit vpa <vpa-name>
```
### Delete hpa/vpa
```yaml
kubectl delete hpa <hpa-name>
kubectl delete hpa <hpa-name> -n <namespace>
kubectl delete vpa <vpa-name>
kubectl delete vpa <vpa-name> -n <namespace>
```
