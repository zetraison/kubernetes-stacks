# Kubernetes Log Aggregation Using ELK Stack

## Create namespace

```bash
kubectl create namespace development
```

## Elasticsearch

### Add the service account, the cluster role and the cluster role binding

```bash
kubectl apply -f elasticsearch-rbac.yml
```

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

### Installing Logstash

```bash
kubectl apply -f configmaps/logstash.yml
kubectl apply -f deployments/logstash.yml
kubectl apply -f services/logstash.yml
```

## Filebeat

### Installing Filebeat

```bash
kubectl apply -f filebeat.yml
```