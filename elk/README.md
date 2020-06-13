# Kubernetes Log Aggregation Using ELK Stack

## Create namespace

```bash
kubectl create namespace development
```

### Add the service account, the cluster role and the cluster role binding

```bash
kubectl apply -f rbac.yml
```

## Elasticsearch

### Installing Elasticsearch

```bash
kubectl apply -f statefulsets/elasticsearch.yml
kubectl apply -f services/elasticsearch.yml
```

### Expose Elasticsearch port

```bash
kubectl port-forward -n development svc/elasticsearch-logging 9200:9200
```

## Logstash

```bash
kubectl apply -f configmaps/logstash.yml
kubectl apply -f deployments/logstash.yml
kubectl apply -f services/logstash.yml
```