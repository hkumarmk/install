This script will install temporal with separate cassandra cluster.
Currently cassandra cluster is deployed in a namespace `cass-operator` and temporal is installed in `temporal` namespace.

## Requirements:
* Install and setup `kubectl`
* Install `helm` commandline client
* Install `uuidgen` command - `apt install uuid-runtime`
* Install `yq` to manipulate yaml - `pip3 install yq`

## How to run this script?
This script has default values that may work for minikube.
You may have to update below variables by creating an env file with values to be overridden
source that env file and run this script.
This script must be executed under the directory where temporal helm chart repository is checked out

### Example:
```
$ git checkout https://github.com/temporalio/helm-charts.git temporal-helm-charts
$ cd temporal-helm-charts/
$ source ../install/sample.env; ../install/install.sh
# Where my_setup.env contain any overridden environment variables
```

## Env variables that may be overridden
Default variables shall work for minikube, which may be overridden to work with other environments. See [sample.env](sample.env) file for reference.
| Variable Name | Description |
| :--- | :--- |
| CASSANDRA_CLUSTER_NAME | cassandra cluster name, default `cluster1` |
| CASSANDRA_STORAGE_CLASS | Cassandra storage class name, default `standard`
| CASSANDRA_STORAGE_SIZE |  Cassandra storage size, default `500Mi`
| CASSANDRA_DC_NAME  | Cassandra datacenter name, default `dc1`
| CASSANDRA_REPLICATION_FACTOR | Cassandra replication factor, default `1`
| CASSANDRA_CLUSTER_SIZE | Cassandra cluster size, default `1`
| TEMPORAL_RELEASE_NAME | Helm release name - only need to check if you run multiple temporal releases, default `t1`|