# Kubernetes

```shell
kubectl run messaging --image=rabbitmq:3.9-alpine --dry-run=client -o yaml > rabbit-pod.yml
kubectl apply -f rabbit-pod.yml
```