# Percona Distribution For MySQL Operator

[Percona XtraDB Cluster (PXC)](https://www.percona.com/doc/percona-xtradb-cluster/LATEST/index.html) is a database clustering solution for MySQL. Percona Distribution for MySQL Operator allows users to deploy and manage Percona XtraDB Clusters on Kubernetes.

Useful links
* [Operator Github repository](https://github.com/percona/percona-xtradb-cluster-operator)
* [Operator Documentation](https://www.percona.com/doc/kubernetes-operator-for-pxc/index.html)

## Pre-requisites
* Kubernetes 1.17+
* Helm v3

# Installation

This chart will deploy the Operator Pod for the further Percona XtraDB Cluster creation in Kubernetes.

## Installing the Chart
To install the chart with the `pxc` release name using a dedicated namespace (recommended):

```sh
helm repo add percona https://percona.github.io/percona-helm-charts/
helm install my-operator percona/pxc-operator --version 1.10.0 --namespace my-namespace
```

The chart can be customized using the following configurable parameters:

| Parameter                       | Description                                                             | Default                                          |
| ------------------------------- | ------------------------------------------------------------------------| -------------------------------------------------|
| `image`                         | PXC Operator Container image full path                                  | `percona/percona-xtradb-cluster-operator:1.10.0` |
| `imagePullPolicy`               | PXC Operator Container pull policy                                      | `Always`                                         |
| `imagePullSecrets`              | PXC Operator Pod pull secret                                            | `[]`                                             |
| `replicaCount`                  | PXC Operator Pod quantity                                               | `1`                                              |
| `tolerations`                   | List of node taints to tolerate                                         | `[]`                                             |
| `resources`                     | Resource requests and limits                                            | `{}`                                             |
| `nodeSelector`                  | Labels for Pod assignment                                               | `{}`                                             |

Specify parameters using `--set key=value[,key=value]` argument to `helm install`

Alternatively a YAML file that specifies the values for the parameters can be provided like this:

```sh
helm install pxc-operator -f values.yaml percona/pxc-operator
```

## Deploy the database

To deploy Percona XtraDB Cluster run the following command:

```sh
helm install my-db percona/pxc-db
```

See more about Percona XtraDB Cluster in its chart [here](https://github.com/percona/percona-helm-charts/blob/main/charts/pxc-db) or in the [Helm chart installation guide](https://www.percona.com/doc/kubernetes-operator-for-pxc/helm.html).
