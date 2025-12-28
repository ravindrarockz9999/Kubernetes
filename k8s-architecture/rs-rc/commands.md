# Kubernetes ReplicaSet & ReplicationController Commands
# ReplicaSet
## 1. Create & Apply
```yaml
kubectl apply -f rs.yaml                                                                                   # Declarative way
kubectl create rs <rs-name> --image=<image-name> --replicas=<number-of-replicas> --port=<container-port>   # Imperative way 
kubectl apply -f replicaset.yaml --dry-run=client
kubectl apply -f replicaset.yaml --dry-run=client -o yaml                                                  
kubectl apply -f replicaset.yaml --dry-run=client -o yaml > rs.yaml 
```
## 2. View RS
```yaml
kubectl get rs
```
## 3. Scale RS
```yaml
kubectl scale rs <rs-name> --replicas=5
```
## 4. Delete RS
```yaml
kubectl delete rs <rs-name>
```
## 5. Describe RS
```yaml
kubectl describe rs <rs-name>
```
# ReplicationController
## 1. Create & Apply
```yaml
kubectl apply -f rc.yaml                                                                                   # Declarative way
kubectl create rc <rc-name> --image=<image-name> --replicas=<number-of-replicas> --port=<container-port>   # Imperative way 
kubectl apply -f replicationcontroller.yaml --dry-run=client
kubectl apply -f replicationcontroller.yaml --dry-run=client -o yaml                                                  
kubectl apply -f replicationcontroller.yaml --dry-run=client -o yaml > rs.yaml 
```
## 2. View RC
```yaml
kubectl get rc
```
## 3. Scale RC
```yaml
kubectl scale rc <rc-name> --replicas=5
```
## 4. Delete RC
```yaml
kubectl delete rc <rc-name>
```
## 5. Describe RC
```yaml
kubectl describe rc <rc-name>
```
