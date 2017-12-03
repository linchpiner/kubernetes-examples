# ELK

## Elasticsearch

    kubectl create -f es-discovery-svc.yaml
    kubectl create -f es-svc.yaml
    kubectl create -f es-master.yaml

    kubectl create -f es-client.yaml
    kubectl create -f es-data.yaml

## Kibana

    kubectl create -f kibana.yaml
    kubectl create -f kibana-svc.yaml

## Logstash

    kubectl create -f logstash.yaml
    kubectl create -f logstash-svc.yaml

