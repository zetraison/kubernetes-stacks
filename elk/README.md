# Kubernetes Log Aggregation Using ELK Stack

## Create namespace

```bash
kubectl create namespace development
```

## Add the service account, the cluster role and the cluster role binding

```bash
kubectl apply -f rbac.yml
```

## Installing Elasticsearch

```bash
kubectl apply -f statefulsets/elasticsearch.yml
kubectl apply -f servicess/elasticsearch.yml
```

## Expose port

```bash
kubectl port-forward -n kube-system svc/elasticsearch-logging 9200:9200
```