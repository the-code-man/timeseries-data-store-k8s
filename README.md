# Timeseries Data Store hosted on kubernetes

## Direct Install

Apply all the manifests defined in objects folder.

### Pre-requisites

The micro services use rabbitmq as the default message broker. RabbitMQ provides a k8s Operator which provides a consistent and easy way to deploy RabbitMQ clusters to kubernetes and run them. Visit the following link (https://www.rabbitmq.com/kubernetes/operator/operator-overview.html) for detailed instructions on how to install and use it.