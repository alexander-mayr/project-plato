# project-plato
Demo Project

# Setup

Tested on minikube on Linux. For the network policies to work, minikube needs to be installed with Calico:

`minikube start --network-plugin=cni --cni=calico`

## Installation

```
helm dependency build
helm install project-plato . -n project-plato --create-namespace=true -f values.yaml -f image.production.yaml
```

## UI

Grafana can be access by

`minikube service project-plato-grafana -n project-plato`

On a remote Cluster this would be achieved by kubectl port-forward or - if it should be made available to users without kubectl - with an additional Ingress controller and an appropriate Ingress object.   
The default login credentials are username `admin` and password `prom-operator`.   
Postgres metrics can be viewed in the metrics explorer. For real world use a dashboard should be created to visualize the metrics data.   
