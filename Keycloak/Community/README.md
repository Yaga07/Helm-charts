helm install my-release oci://registry-1.docker.io/bitnamicharts/keycloak


REFERENCE

https://github.com/bitnami/charts/tree/main/bitnami/keycloak


-------------------------------------------------------------
# My Helm Chart

A Helm chart for deploying **My Application** on Kubernetes.

## Prerequisites

- Kubernetes 1.20+
- Helm 3.0+
- (Optional) Ingress Controller for enabling Ingress resources
- PersistentVolume provisioner for stateful applications

## Installation

To install the chart with the release name `my-release`:

```bash
helm install my-release ./my-chart
```
This command deploys the chart using the default values. You can customize the installation by specifying custom values:

```bash
helm install my-release ./my-chart -f values.yaml
```

Configuration
The following table lists the configurable parameters of the chart and their default values:

| Key                   | Type   | Default         | Description                                          |
|-----------------------|--------|-----------------|------------------------------------------------------|
| `replicaCount`        | int    | `1`             | Number of replicas for the deployment                |
| `image.repository`    | string | `my-image`      | The image repository for the application             |
| `image.tag`           | string | `latest`        | The image tag to use                                 |
| `image.pullPolicy`    | string | `IfNotPresent`  | Image pull policy                                    |
| `service.type`        | string | `ClusterIP`     | Kubernetes service type (e.g., ClusterIP, NodePort, LoadBalancer) |
| `service.port`        | int    | `80`            | The port the service will listen on                  |
| `ingress.enabled`     | bool   | `false`         | Enable ingress for the application                   |
| `ingress.annotations` | object | `{}`            | Annotations for the ingress                          |
| `ingress.hosts`       | list   | `[]`            | List of hosts for the ingress                        |
| `ingress.tls`         | list   | `[]`            | TLS configuration for the ingress                    |


For the full list of available values, see the values.yaml file.
Upgrading

To upgrade the chart, use:

```bash

helm upgrade my-release ./my-chart
```
If you made changes to values.yaml, you can include the updated file:

```bash

helm upgrade my-release ./my-chart -f values.yaml
```
Uninstalling the Chart

To uninstall/delete the my-release deployment:

```bash
helm uninstall my-release
```
This command removes all the Kubernetes resources associated with the release and deletes the release from Helm's history.
Persistence

The chart can use Persistent Volume Claims (PVCs) to persist data. By default, PVCs are enabled. To disable persistence, set the following value in values.yaml:

```yaml
persistence:
  enabled: false
```
To customize the PVC, you can use the following options:
Key	Type	Default	Description
persistence.size	string	8Gi	The size of the PVC
persistence.storageClass	string	""	The storage class to use for the PVC
Notes

    Ensure that the specified ingress.hosts values match your domain if you are using Ingress.
    If you are using a private image repository, make sure to configure image pull secrets.

Contributing

Feel free to submit issues and enhancement requests. If you'd like to contribute, please fork the repository and submit a pull request.
