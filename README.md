# Kubernetes

[![Lint](https://github.com/rafalski76/kubernetes/actions/workflows/lint.yml/badge.svg)](https://github.com/rafalski76/kubernetes/actions/workflows/lint.yml)

Proste manifesty Kubernetesa do nauki podstawowych obiektów: Pod, ConfigMap i Secret.

## Wymagania

- działający klaster (np. [kind](https://kind.sigs.k8s.io/), minikube, Docker Desktop lub klaster z repozytorium [vagrant](https://github.com/rafalski76/vagrant))
- `kubectl`

## Zawartość

| Katalog | Opis |
| --- | --- |
| `alpine/` | Pod `alpine`, który wypisuje zmienne środowiskowe pochodzące z ConfigMap (`configmap.yml`) i Secret (`secret.yml`) |
| `rabbit/` | Pod z brokerem RabbitMQ (`rabbitmq:4-alpine`) |

## Użycie

```shell
# RabbitMQ
kubectl run messaging --image=rabbitmq:4-alpine --dry-run=client -o yaml > rabbit/pod.yml   # (opcjonalnie) wygenerowanie manifestu
kubectl apply -f rabbit/pod.yml

# Alpine z ConfigMap i Secret
kubectl apply -f alpine/configmap.yml
kubectl apply -f alpine/secret.yml
kubectl apply -f alpine/pod.yml
kubectl logs alp-pod        # zmienne GREETINGS_FROM i PASSWORD

# Sprzątanie
kubectl delete -f alpine/ -f rabbit/
```

> Wartość w `secret.yml` jest zakodowana w base64, a nie zaszyfrowana. To przykład edukacyjny –
> prawdziwych sekretów nie należy przechowywać w repozytorium.

## Lint / CI

Workflow [`lint.yml`](.github/workflows/lint.yml) uruchamia `yamllint` oraz `kubeconform`
(walidacja manifestów względem schematów Kubernetesa).
