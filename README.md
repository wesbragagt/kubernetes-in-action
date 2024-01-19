# Kubernetes in Action Practice

## Reference

### Pods

short: po

A pod can be a single container or a group of containers running within a Kubernetes Cluster. Pods also have their unique IP address within the cluster.

### Nodes

short: no 

Worker machines that kubernetes uses to assign pods to run workloads. The kubernetes scheduler is responsible for assigning pods to nodes.

### Services

short: svc

In order to expose our applications running inside pods to the outside world, we need to create a service. A service is a kubernetes object that acts as a load balancer for pods running on the cluster. A service can be exposed in different ways by specifying a type in the service definition:

- ClusterIP: Exposes the service on a cluster-internal IP. Choosing this value makes the service only reachable from within the cluster. This is the default ServiceType.
- LoadBalancer: Exposes the service externally using a cloud provider’s load balancer.

### Replication Controllers

short: rc

Responsible for managing the amount of pods running at any given time. Default to 1 pod.

Example command: `kubectl run my-app --image=my-app-image --port=8080 --generator=run/v1` - --generator flag creates a replication controller instead of a deployment.
