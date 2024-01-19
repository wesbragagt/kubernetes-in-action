# Exercise 1

- [x] 1. Build a container image for the application
- [x] 2. Push this container image to a public registry
- [x] 3. Within our kubernetes cluster run the application using the ReplicationController
- [x] 4. Expose the application using a Service
- [x] 5. Scale the application using the ReplicationController to 3 instances

## Cheat Sheet

### Create a Kind cluster

```
kind create cluster --name=k8-in-action
```

Change the context to the new cluster
```
kubectl config use-context k8-in-action
```

### Create Pods
Creates our pods with the replication controller
```
kubectl apply -f replication-controller.yaml
```

### Creates our service
```
kubectl expose rc test-node-app-rc --type=LoadBalancer --port=4000 --target-port=80
```

port: 4000 - port on the node
target-port: 80 - port on the container

type: LoadBalancer - exposes the service externally using a cloud provider’s load balancer.

Given we are using a local kubernetes cluster there is no external load balancer. Instead we can use the following:

### Exposing the service

```
kubectl port-forward svc/test-node-app-rc 4000:4000
```

This will forward traffic from port 4000 on our host to port 4000 on the service.

On a cloud provider like AWS we would use an AWS Load Balancer to route traffic to our service.
