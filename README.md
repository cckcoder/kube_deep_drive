# Learning Kube from acloud.guru

## Resource

[github](https://github.com/ACloudGuru-Resources/Course_Kubernetes_Deep_Dive_NP/tree/master/sample-app/mysql-wordpress-pd)

## Kube Big Picture 
* Control plane (Master Node)
  * etcd
    * Stateful
  * api
    * For CRUD
      * `kubectl get pods`
  * scheduler

* Workers (Worker Node)

### The Kube API

`kubectl get apiservices`

* Alpha => User beware (E.g. v1alpha1)
* Beta => Taking shape. Becoming stable (E.g. v2beta1)
* GA => Ready for production (E.g. V1, V2 etc.)

### The Kube Objects

> Pod
  * Colntains one or more container
  * Atomic unit of scheduling

> Deploy
  * Scalability and application releases
  * Object on the cluster
  * Defined in the apps/v1 API group
  * Scaling
  * Rolling updates

> One Pod per node

> Stateful app components

## Kube Networking

* Common Networking Requirements
* Networking in the Sample App
* Kube Networking basic
* Service
* Service Types
* The Service Network
* Lab
* Summary

### House Rules
* All Nodes can talk
* All Pods can talk (No NAT)
* Every Pod gets it's own IP

![kube-network](./image/kube-network-basic.png)

### Service
![kube-service](./image/kube-services.png)

* Every service have
  * Name
  * IP
  > Stable neverchange name and IP whole life

#### Service Type

* ClusterIP (default)
  * Gets own IP
  * Only accessible from within cluster

* NodePord
  * Gets cluster-wide port
  * Also accessible from outside of cluster
![kube-nodepord](./image/kube-node-port.png)
  
* LoadBalancer
  * Integrates with public cloud platform

> Get CIDR
`k get no -o jsonpath='{.items[*].spec.podCIDR}'`

### DEMO1
* access to Pod `kubectl exec <POD_NAME> bash`
* update ubuntu in Pod `apt-get update -y`
* install few tools
  * `apt-get install -y iputils-ping curl dnsutils iproute2`

> Connect to NodePort

* <SERVICE_NAME>:<PORT>
  * `curl hello-svc:8080`

* <NODE_IP>:<NODE_PORT>
  * `curl 172.18.0.3:30001`
