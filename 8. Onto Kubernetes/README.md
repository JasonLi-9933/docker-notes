# Comparisons

| Docker Compose                                                 | Kubernetes                                        | Get a container running locally inK8S          |
| -------------------------------------------------------------- | ------------------------------------------------- | ---------------------------------------------- |
| Each entry can optionally get docker-compose to build an image | Kubernetes expects all images to already be built | Make sure our image is hosted on docker hub    |
| Each entry represents a container we want to create            | One config file per object we want to create      | Make onr config file to create the "container" |
| Each entry defines the networking requirements (ports)         | We have to manually set up all networking         | Make one config file to set up networking      |

# Inside K8S clusters

There is a _master_ program in charge of monitoring/updating the _node(s)_. Each node can be a VM and we run containers inside nodes.

# What the config yml files used for?

The `kubectl` will use the config file to create 'objects'
An object is a thing that exist in k8s cluster.
Object type includes: `StatefulSet`, `ReplicaController`, `Pod`, `Service`. Indicated by `kind` field in the config file.
Objects serve different purposes: running/monitoring containers, setting up networking, etc

# apiVersion: defines a different set of 'objects' we can use

# Type of objects

- Pod

  1. A grouping of containers with common purpose.
  2. A smallest thing to run to deploy a container, k8s cannot run containers alone, a container need to run inside a Pod.
  3. In Pod we group containers that are very tightly coupled.
  4. Has restrictions on updating certain properties (use deployment instead)

- Service

  1. Sets up some type of networking in a Kubernetes Cluster
  2. 4 types: `ClusterIP`, `NodePort`, `LoadBalancer`, `Ingress`
     - `NodePort`: exposes a container to the outside world (only good for dev purpose)
     - `ClusterIP`: Exposes a set of pods to _other objects in the cluster_
     - `LoadBalancer`: Legacy way of getting network traffic into a cluster
     - `Ingress`: Exposes a set of services to the outside world
       Ingress config file (routing rules) is feed into a Ingress Controller then create something that accepts incoming traffic, the Ingress Controller constantly watches changes and make updates to handle traffics.

- Deployment

  1. Maintains a set of identical pods, ensuring that they have the correct config and that the right number exists

- Secrets
  1. Securely stores a piece of information in the cluster, such as a database password
  2. Need to create imperatively with command

# Pods VS Deployment

| Pods                            | Deployment                                                |
| ------------------------------- | --------------------------------------------------------- |
| runs a single set of containers | runs a set of identical pods (one or more)                |
| good for one-off dev purposes   | monitors the state of the each pod, updating as necessary |
| rarely used directly in prod    | good for both dev and prod                                |

# Imperative Development VS Declarative Deployment

- Imperative: Do exactly these step to reach the goal
- Declarative: Our container setup should look like this, make it happen

# _name_ and _kind_ are unique identify tokens to identify existing object (ex: for updating object)

# Why use Services?

The Service object is watching every node with the matching label and automatically direct traffic to the matched nodes.

# How to trigger deployment update after new version of image is pushed to docker hub? (A hard problem)

1. Delete the pod(s) to get the deployment to recreate pods with the latest version
2. Tag built images with a real version number and specify that version in the config file
3. Use an imperative command to update the image version the deployment should use

# Volumes

- In generic container terminology: Some type of mechanism that allows a container to access a filesystem outside itself
- In the world of kubernetes: An **object** that allows a container to store data at the pod level. If pod no longer exist, the data in the volume is also gone, so we want to use _Persistent Volume Claim_ or _Persistent Volume_ in the world of kubernetes for database.
  1. Persistent Volume: Doesn't live within pod, will last all the time
  2. Persistent Volume Claim (PVC): a request for storage by user

| Persistent Volume | Persistent Volume Claim |
| ----------------- | ----------------------- |

|
