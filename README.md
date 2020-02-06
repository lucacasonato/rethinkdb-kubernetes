# RethinkDB on Kubernetes

Running a [RethinkDB](https://rethinkdb.com/) cluster on [Kubernetes](https://kubernetes.io/).

- Super simple - no configuration required
- Runs cluster as a `StatefulSet` which prevents data loss when the cluster unexpectedly shuts down
- Automatic peer discovery using the Kubernetes service

## Quick Start

To create the RethinkDB cluster run this command:

```bash
kubectl create -f https://raw.githubusercontent.com/lucacasonato/rethinkdb-kubernetes/master/cluster.yaml
```

This will set up all of the required Kubernetes resources. You can now use the command below to view if your node is ready:

```bash
kubectl get sts rethinkdb-nodes
```

Your cluster is now ready for operation!

## Advanced usage

### Scaling the cluster

To scale the cluster up and down run this command:

```bash
kubectl scale sts rethinkdb-nodes --replicas 3
```

### Using the admin panel

To view the RethinkDB admin panel you need to forward the port it is listening on to your computer. You can do this from any of the running RethinkDB nodes in the stateful set.

```bash
kubectl port-forward rethinkdb-nodes-0 8080
```

You can now visit `http://localhost:8080` to view the admin panel.

## Licence

Copyright (c) 2020 Luca Casonato

This project is licenced under the MIT licence. The full licence can be found in the LICENCE file.
