# Kubernetes

```shell
kubectl run messaging --image=rabbitmq:3.9-alpine --dry-run=client -o yaml > pod.yml
kubectl apply -f pod.yml
```