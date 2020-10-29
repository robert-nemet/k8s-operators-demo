# K8s operators

`Operators` are software extensions to Kubernetes that make use of custom resources to manage applications and their components. Operators follow Kubernetes principles, notably the control loop.

`A resource` is an endpoint in the Kubernetes API that stores a collection of API objects of a certain kind.

`Custom resources` are extensions of the Kubernetes API.

`A declarative API` allows you to declare or specify the desired state of your resource and tries to keep 
the current state of Kubernetes objects in sync with the desired state.

`The controller` interprets the structured data as a record of the user's desired state, and continually maintains this state.

## Why Operator

Recording repeatable manual steps executed by the human operator like:
 * deploying a service on demand
 * backups and restoring backups
 * simulate a failure as part of resilience testing
 * simulate heavy load for load testing 
 
## How

**Operator pattern** is a combination of *custom resources* and *custom controllers*. 

### Two ways: the API aggregation

  - integrate custom API in k8s aggregation layer(API server is behind k8s API proxy)
  - detailed and grained process control (full control)
  - programming 
  - maintenance like any other app
  - flexible security

### Two ways: CRDs

 - no programming for CRD
 - program just controller (simple webhooks)
 - no custom storage
 - no PATCH
 - no logs

## Frameworks

It is complicated as one need to define proper CRD or API and to follow complicated rules and schemas

### [KUDO](https://kudo.dev/) (Kubernetes Universal Declarative Operator)

 - declarative
 - feels like writing yaml configuration
 - KUDO operator and KUDO CRD => specific operator
 - repository of operators
 - testing ability
 - opinionated way to develop operator: focus on life cycle
 - no need for programming skills

### [Metacontroller](https://metacontroller.app/)

 - webhooks
 - easy to define behaviour of CRDs
 - could be complex for managing operator life cycle
 - more freedom than the KUDO
 
### [Kubebuilder](https://github.com/kubernetes-sigs/kubebuilder)

 - building k8s APIs with CRDs
 - requires knowledge of the Go
 - opinionated way to develop operator
 
### [Operator framework](https://sdk.operatorframework.io/)
 
 - support for full and detailed control for developing operator
 - support for full control over operator life cycle
 - work with Helm and Ansible
 - Go, Helm or Ansible
 - all you ever need to make and manage operator
 
## Do I need operator?

 * Repeatable operations initiated by services(like scheduled backups)
   which are not supported by the platform.
 * Organization specific repeatable tasks
 * Costly: developers, resources, architecture
 * Recommended for a specific services which adds missing features to the platform 


