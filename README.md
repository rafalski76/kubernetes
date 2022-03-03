# Kubernetes

```shell
kubectl run messaging --image=rabbitmq:3.9-alpine --dry-run=client -o yaml > rabbit/pod.yml
kubectl apply -f rabbit/pod.yml

kubectl apply -f alpine/configmap.yml
kubectl apply -f alpine/secret.yml
kubectl apply -f alpine/pod.yml
```