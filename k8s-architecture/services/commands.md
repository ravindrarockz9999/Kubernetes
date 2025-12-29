# Kubernetes Service Commands

## 1. Create / Apply Services
```yaml
kubectl create -f service.yaml                                                          # Declarative way to create
kubectl apply -f service.yaml                                                           # Declarative way to create and reapply
kubectl expose deployment <deploy-name> --name=<svc-name> --port=80 --target-port=8080  # Imperative way to create
kubectl expose deployment my-app --type=NodePort --name=<svc-name> --port=80            # Imperative way to create svc type nodePort
kubectl expose deployment my-app --type=LoadBalancer --name=<svc-name> --port=80        # Imperative way to create svc type loadBalancer
```
## 2. Update Services
```yaml
kubectl edit service <service-name>
```
## 3. Get / Describe the Pod
```yaml
kubectl get svc
kubectl get svc --all-namespaces            # To get All services in all namespaces
kubectl get svc -n <namespace-name>         # To get particular namespace
kubectl get svc -o wide
kubectl get service <service-name> -o yaml
kubectl describe service <service-name>
```
## 4. Delete Services
```yaml
kubectl delete service <service-name>
kubectl delete -f service.yaml              # Delete using yaml
kubectl delete svc --all
kubectl delete svc --all -n <namespace>
```
## 5. Services Endpoints
```yaml
kubectl get ep                              # Inshot for endpoints we can use both
kubectl get endpoints <service-name>
kubectl get pods -l app=my-app              # List pods selected by service
```
## 6. Access & Networking
```yaml
kubectl port-forward service/<service-name> 8080:80     # Service Port forward
```
