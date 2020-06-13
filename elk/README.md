# Kubernetes Log Aggregation Using ELK Stack

## Create namespace

```bash
kubectl create namespace elk
```

## Elasticsearch

### Installing Elasticsearch

```bash
kubectl apply -f elasticsearch.yml
```

### Expose Elasticsearch port

```bash
kubectl port-forward -n development svc/elasticsearch-logging 9200:9200
```

## Logstash

### Installing Logstash

```bash
kubectl apply -f logstash.yml
```

## Filebeat

### Installing Filebeat

```bash
kubectl apply -f filebeat.yml
```

## Kibana

### Installing Kibana

```bash
kubectl apply -f kibana.yml
```