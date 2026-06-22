# Kubernetes Commands

**Source**: Custom workspace skill

Manage Kubernetes clusters and workloads.

## Context & Config

```bash
# List contexts
kubectl config get-contexts

# Switch context
kubectl config use-context prod-cluster

# Current context
kubectl config current-context

# View config
kubectl config view
```

## Namespaces

```bash
kubectl get namespaces
kubectl create namespace myapp
kubectl delete namespace myapp
kubectl config set-context --current --namespace=myapp
```

## Pods

```bash
# List pods
kubectl get pods
kubectl get pods -n myapp
kubectl get pods --all-namespaces

# Pod details
kubectl get pod mypod -o wide
kubectl describe pod mypod

# Logs
kubectl logs mypod
kubectl logs -f mypod              # Follow
kubectl logs --previous mypod      # Previous container
kubectl logs mypod -c container     # Specific container

# Execute
kubectl exec -it mypod -- /bin/bash
kubectl exec -it mypod -- sh

# Delete
kubectl delete pod mypod
```

## Deployments

```bash
# List
kubectl get deployments
kubectl get deployment myapp -o wide

# Scale
kubectl scale deployment myapp --replicas=3

# Rolling update
kubectl rollout undo deployment/myapp
kubectl rollout status deployment/myapp

# Restart
kubectl rollout restart deployment/myapp

# Image update
kubectl set image deployment/myapp container=nginx:v2
```

## Services

```bash
kubectl get services
kubectl get svc
kubectl describe service myservice

# Create
kubectl expose deployment myapp --port=80 --target-port=8080

# Port forward (local dev)
kubectl port-forward svc/myapp 8080:80

# Delete
kubectl delete service myservice
```

## ConfigMaps & Secrets

```bash
kubectl get configmaps
kubectl get secrets

# Create from literal
kubectl create configmap myconfig --from-literal=key=value
kubectl create secret generic mysecret --from-literal=password=secret

# From file
kubectl create configmap myconfig --from-file=config.yaml
kubectl create secret generic mysecret --from-file=.env
```

## Ingress

```bash
kubectl get ingress
kubectl describe ingress myingress

# Create
kubectl apply -f ingress.yaml
```

## Troubleshooting

```bash
# All resources
kubectl get all -n myapp

# Events
kubectl get events
kubectl get events --sort-by='.lastTimestamp'

# Top resources
kubectl top pod
kubectl top node

# Explain
kubectl explain pod
kubectl explain deployment.spec
```

---

*Install date: 2026-04-27*
