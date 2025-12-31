# Kubernetes Taint & Tolerations Commands:

## Taints
```yaml
kubectl taint nodes <node-name> <key>=<value>:<effect>
```
### Example
```bash
kubectl taint nodes node1 env=prod:NoSchedule   # Node node1 is tainted so that only Pods that toleration env=prod can be scheduled. Here Full restriction.
kubectl taint nodes node2 app=frontend:PreferredNoSchedule   # Node node2 is tainted so that Pods that toleration app=frontend can be scheduled.If any other nodes not present ie will allow to schedule, Here pacital restriction.
kubectl taint nodes node3 gpu=true:NoExecute    # Bit dangerous all pods will stop ruiing unless they have tolerations, mostly use in cluster upgrades
```

## Toleration
### Ex-1
```yaml
  tolerations:
  - key: "env"
    operator: "Equal"      # Here env=prod and effect is check if eveything is correct then place the pod to node1
    value: "prod"
    effect: "NoSchedule"
```
### Ex-2
```yaml
tolerations:
- key: "env"
  operator: "Exists"      # Here just check key and effect if env is ther in taint even the value is empty it will place the pod to pod1
  effect: "NoSchedule"
```
