# Kubernetes Secrets Commands

## 1. Create Secrets in imperative way

### a) Create Generic Secret (Opaque) from literal values

```bash
kubectl create secret generic app-secret \
  --from-literal=DB_USER=admin \
  --from-literal=DB_PASSWORD=password
```
### b) Create Secret from a file
```bash
kubectl create secret generic app-secret \
  --from-file=app.properties \
  --from-file=credentials.txt
```
### c) Create Docker Registry Secret
```bash
kubectl create secret docker-registry regcred \
  --docker-server=<registry-server> \
  --docker-username=<username> \
  --docker-password=<password> \
  --docker-email=<email>
```
### d) Create TLS Secret
```bash
kubectl create secret tls tls-secret \
  --cert=path/to/tls.crt \
  --key=path/to/tls.key
```
### e) Create Service Account
```bash
kubectl create serviceaccount my-app-sa
```
### f) create secret in declarative way
```bash
kubectl apply -f secret.yaml
```
## 2. View Secrets
```bash
kubectl get secrets
kubectl get secret app-secret -o yaml    # export secret in json file format
kubectl describe secret app-secret
```
## 3. Edit/delete secret
```bash
kubectl edit secret app-secret
kubectl delete secret app-secret
```




  
