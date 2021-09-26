# Timeseries Data Store hosted on kubernetes

## Pre-requisites

### Rabbitmq 

1) The application uses rabbitmq as the default message broker. RabbitMQ provides a k8s Operator which provides a consistent and easy way to deploy RabbitMQ clusters to kubernetes and run them. Visit the following link (https://www.rabbitmq.com/kubernetes/operator/operator-overview.html) for detailed instructions on how to install and use it.

2) Current setup also uses rabbitmq messaging topology operator to install objects like vhost, users, permissions etc. Visit the following link https://www.rabbitmq.com/kubernetes/operator/install-topology-operator.html.

3) Before provisioning Rabbitmq cluster install **Physical Volume Provisioner**. Otherwise PODS will be forever in pending state. For non-production environment, we can use Local Path Provisioner provided by Rancher (https://github.com/rancher/local-path-provisioner). Check https://www.rabbitmq.com/kubernetes/operator/quickstart-operator.html. Basically we have to apply the following:

```bash
kubectl apply -f https://raw.githubusercontent.com/rancher/local-path-provisioner/master/deploy/local-path-storage.yaml
kubectl annotate storageclass local-path storageclass.kubernetes.io/is-default-class=true
```

### Ingress

1) TLS - Generate a self-signed certificate for ingress resource. Example --> 

```bash
openssl req -x509 -newkey rsa:4096 -sha256 -nodes -keyout tsdatastoreapp.key -out tsdatastoreapp.crt -subj "/CN=tsdatastoreapp.com"
```
## Direct Install

Apply all the manifests defined in objects folder in the provided order.

## Helm

WIP