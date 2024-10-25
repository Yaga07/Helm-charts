# Nginx Ingress Helm Chart

A Helm chart for deploying **Nginx Ingress** on Kubernetes.

## Prerequisites

- Kubernetes 1.20+
- Helm 3.0+
- (Optional) Ingress Controller for enabling Ingress resources

## Installation
Add Helm Repo of Nginx Ingress

```bash
helm repo add nginx https://helm.nginx.com/stable
```

Install the chart of `Nginx-Ingress`:

```bash
 helm install nginx -n ingress nginx/nginx-ingress -f values.yaml --create-namespace=true
```
This command deploys the chart using the custom values. You can customize the installation by specifying custom values:

Configuration
The following table lists the configurable parameters of the chart and their updated values:

| Key                      | Type   | Default               | Description                                          |
|--------------------------|--------|-----------------------|------------------------------------------------------|
| `replicaCount`           | int    | `1`                   | Number of replicas for the deployment                |
| `image.repository`       | string | `nginx/nginx-ingress` | The image repository for the application             |
| `image.tag`              | string | `3.2.0`               | The image tag to use                                 |
| `image.pullPolicy`       | string | `IfNotPresent`        | Image pull policy                                    |
| `service.type`           | string | `NodePort`            | Kubernetes service type (e.g., ClusterIP, NodePort, LoadBalancer) |
| `service.port`           | int    | `80`                  | The port the service will listen on                  |
| `controller.hostNetwork` | bool   | `true`                | Enable ingress to use host network                   |
| `controller.resources`   | object | `{}`                  | resource allocation or limit                         |
| `controller.ingressClass`| string | `nginx`               | ingress class name                                   |



For the full list of available values, see the values.yaml file.
Upgrading

To upgrade the chart, use:

```bash

 helm upgrade --install nginx -n ingress nginx/nginx-ingress -f values.yaml 
```

Uninstalling the Chart

To uninstall/delete the Nginx-Ingress deployment:

```bash
helm uninstall nginx -n ingress
```
This command removes all the Kubernetes resources associated with the release and deletes the release from Helm's history.

Reference
```bash
https://helm.nginx.com/
https://github.com/nginxinc/kubernetes-ingress/blob/main/charts/nginx-ingress/values.yaml
```


Contributing

Feel free to submit issues and enhancement requests. If you'd like to contribute, please fork the repository and submit a pull request.
