# Learning Kube from acloud.guru

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
