# ELK

## Deployment

The recommendation is to use a dedicated Kubernetes namespace

    kubectl create namespace elk
    kubectl config set-context elk --cluster=kubernetes --user=kubernetes-admin --namespace=elk
    kubectl config use-context elk

### Elasticsearch

    kubectl create -f es-discovery-svc.yaml
    kubectl create -f es-svc.yaml
    kubectl create -f es-master.yaml

    kubectl create -f es-data.yaml

### Kibana

    kubectl create -f kibana.yaml
    kubectl create -f kibana-svc.yaml

### Logstash

    kubectl create -f logstash.yaml
    kubectl create -f logstash-svc.yaml

## Tear Down

If the ELK cluster is deployed in a dedicated namespace, then the simples way to tear down ELK is to delete a namespace:

    kubectl delete namespace elk
    kubectl config use-context kubernetes-admin@kubernetes

Otherwise, you can delete all the ELK resources:

    kubectl delete svc elasticsearch elasticsearch-discovery kibana logstash
    kubectl delete rc logstash
    kubectl delete deployment es-data es-master kibana

