# Grafana en Kubernetes con Deployment y ReplicaSet

Tarea individual: despliegue de **Grafana** en un clúster local de **Minikube** aplicando los conceptos de **Deployment** y **ReplicaSet**, y exposición mediante un **Service NodePort**.

## Requisitos

- Docker Desktop
- Minikube
- kubectl

## Despliegue

```bash
minikube start
kubectl apply -f .
kubectl get deployments
kubectl get rs
kubectl get pods -l app=grafana -o wide
minikube service grafana-svc
```

Credenciales: `admin` / `udla2026`

## Demostraciones realizadas

```bash
# Autorreparación (ReplicaSet)
kubectl delete pod <nombre-del-pod>

# Escalado
kubectl scale deployment grafana --replicas=5
kubectl scale deployment grafana --replicas=3

# Rolling update (Deployment)
kubectl set image deployment/grafana grafana=grafana/grafana:12.2.0
kubectl rollout status deployment/grafana
kubectl rollout history deployment/grafana

# Rollback
kubectl rollout undo deployment/grafana
```

## Limpieza

```bash
kubectl delete -f .
minikube stop
```
