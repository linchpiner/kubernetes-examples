# ELK

## Deploy

Must be used in the 'default' namespace.
The current Logstash configuration is expecting logstash-forwarder to be its log input 
and the certificates provided are valid only for `logstash.default.svc.cluster.local`.

### Elasticsearch

    kubectl create -f es-discovery-svc.yaml
    kubectl create -f es-svc.yaml
    kubectl create -f es-master.yaml

### Kibana

    kubectl create -f kibana.yaml
    kubectl create -f kibana-svc.yaml

### Logstash

    kubectl create -f logstash.yaml
    kubectl create -f logstash-svc.yaml

## Tear Down

    kubectl delete svc elasticsearch elasticsearch-discovery kibana logstash
    kubectl delete rc logstash
    kubectl delete deployment es-master kibana

